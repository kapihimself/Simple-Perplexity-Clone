# 🚀 Deployment Guide

This guide covers different deployment options for the AI Assistant (Perplexity Clone) application.

## 🌐 Vercel (Recommended)

Vercel is the easiest way to deploy Next.js applications and is created by the same team.

### Prerequisites
- GitHub account
- Vercel account (free tier available)
- Repository pushed to GitHub

### Steps
1. **Connect Repository**
   - Go to [Vercel Dashboard](https://vercel.com/dashboard)
   - Click "New Project"
   - Import your GitHub repository

2. **Configure Environment Variables**
   Add these environment variables in Vercel dashboard:
   ```
   DATABASE_URL=your-production-database-url
   NEXTAUTH_URL=https://your-domain.vercel.app
   NEXTAUTH_SECRET=your-production-secret
   OPENAI_API_KEY=your-openai-key
   GEMINI_API_KEY=your-gemini-key
   MIDTRANS_MERCHANT_ID=your-merchant-id
   MIDTRANS_CLIENT_KEY=your-client-key
   MIDTRANS_SERVER_KEY=your-server-key
   MIDTRANS_IS_PRODUCTION=true
   ```

3. **Database Setup**
   - For production, use PostgreSQL or PlanetScale
   - Update `DATABASE_URL` to your production database
   - Run migrations: `npx prisma db push`

4. **Deploy**
   - Click "Deploy"
   - Vercel will automatically build and deploy your app

### Automatic Deployments
- Vercel automatically deploys on every push to main branch
- Preview deployments for pull requests
- Rollback functionality available

## 🐳 Docker Deployment

### Dockerfile
Create a `Dockerfile` in your project root:

```dockerfile
# Use Node.js 18 Alpine image
FROM node:18-alpine AS base

# Install dependencies only when needed
FROM base AS deps
RUN apk add --no-cache libc6-compat
WORKDIR /app

# Install dependencies based on the preferred package manager
COPY package.json package-lock.json* ./
RUN npm ci --only=production

# Rebuild the source code only when needed
FROM base AS builder
WORKDIR /app
COPY --from=deps /app/node_modules ./node_modules
COPY . .

# Generate Prisma client
RUN npx prisma generate

# Build the application
RUN npm run build

# Production image, copy all the files and run next
FROM base AS runner
WORKDIR /app

ENV NODE_ENV production

RUN addgroup --system --gid 1001 nodejs
RUN adduser --system --uid 1001 nextjs

COPY --from=builder /app/public ./public

# Automatically leverage output traces to reduce image size
COPY --from=builder --chown=nextjs:nodejs /app/.next/standalone ./
COPY --from=builder --chown=nextjs:nodejs /app/.next/static ./.next/static

USER nextjs

EXPOSE 3000

ENV PORT 3000
ENV HOSTNAME "0.0.0.0"

CMD ["node", "server.js"]
```

### Docker Compose
Create `docker-compose.yml`:

```yaml
version: '3.8'
services:
  app:
    build: .
    ports:
      - "3000:3000"
    environment:
      - DATABASE_URL=${DATABASE_URL}
      - NEXTAUTH_URL=${NEXTAUTH_URL}
      - NEXTAUTH_SECRET=${NEXTAUTH_SECRET}
      - OPENAI_API_KEY=${OPENAI_API_KEY}
      - GEMINI_API_KEY=${GEMINI_API_KEY}
    depends_on:
      - db

  db:
    image: postgres:15
    environment:
      - POSTGRES_DB=perplexity_clone
      - POSTGRES_USER=postgres
      - POSTGRES_PASSWORD=password
    volumes:
      - postgres_data:/var/lib/postgresql/data
    ports:
      - "5432:5432"

volumes:
  postgres_data:
```

### Build and Run
```bash
# Build the image
docker build -t perplexity-clone .

# Run with docker-compose
docker-compose up -d
```

## ☁️ Railway

Railway provides an easy deployment platform with database hosting.

### Steps
1. **Connect Repository**
   - Go to [Railway](https://railway.app)
   - Connect your GitHub repository

2. **Add Database**
   - Add PostgreSQL service
   - Railway will provide `DATABASE_URL`

3. **Configure Variables**
   Add environment variables in Railway dashboard

4. **Deploy**
   - Railway automatically builds and deploys

## 🔧 Manual VPS Deployment

### Prerequisites
- Ubuntu/Debian VPS
- Node.js 18+ installed
- Nginx installed
- SSL certificate (Let's Encrypt recommended)

### Steps
1. **Clone Repository**
   ```bash
   git clone https://github.com/yourusername/perplexity-clone.git
   cd perplexity-clone
   ```

2. **Install Dependencies**
   ```bash
   npm install
   ```

3. **Environment Setup**
   ```bash
   # Create production environment file
   cp .env.example .env.production
   # Edit with your production values
   nano .env.production
   ```

4. **Database Setup**
   ```bash
   npx prisma db push
   npx prisma generate
   ```

5. **Build Application**
   ```bash
   npm run build
   ```

6. **Process Manager (PM2)**
   ```bash
   # Install PM2
   npm install -g pm2

   # Start application
   pm2 start npm --name "perplexity-clone" -- start

   # Save PM2 configuration
   pm2 save
   pm2 startup
   ```

7. **Nginx Configuration**
   Create `/etc/nginx/sites-available/perplexity-clone`:
   ```nginx
   server {
       listen 80;
       server_name your-domain.com;

       location / {
           proxy_pass http://localhost:3000;
           proxy_http_version 1.1;
           proxy_set_header Upgrade $http_upgrade;
           proxy_set_header Connection 'upgrade';
           proxy_set_header Host $host;
           proxy_set_header X-Real-IP $remote_addr;
           proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
           proxy_set_header X-Forwarded-Proto $scheme;
           proxy_cache_bypass $http_upgrade;
       }
   }
   ```

8. **Enable Site**
   ```bash
   sudo ln -s /etc/nginx/sites-available/perplexity-clone /etc/nginx/sites-enabled/
   sudo nginx -t
   sudo systemctl reload nginx
   ```

9. **SSL Certificate**
   ```bash
   sudo certbot --nginx -d your-domain.com
   ```

## 📊 Database Options

### PostgreSQL (Recommended for Production)
- **Supabase** - Managed PostgreSQL with real-time features
- **Neon** - Serverless PostgreSQL
- **PlanetScale** - MySQL-compatible serverless database
- **Railway** - Simple PostgreSQL hosting

### Environment Variables for Production
```env
# PostgreSQL example
DATABASE_URL="postgresql://username:password@host:5432/database?schema=public"

# PlanetScale example
DATABASE_URL="mysql://username:password@host:3306/database?sslaccept=strict"
```

## 🔧 Environment Variables

### Required Variables
```env
DATABASE_URL=your-database-url
NEXTAUTH_URL=https://your-domain.com
NEXTAUTH_SECRET=your-secret-key
OPENAI_API_KEY=your-openai-key
GEMINI_API_KEY=your-gemini-key
```

### Optional Variables
```env
MIDTRANS_MERCHANT_ID=your-merchant-id
MIDTRANS_CLIENT_KEY=your-client-key
MIDTRANS_SERVER_KEY=your-server-key
MIDTRANS_IS_PRODUCTION=true
NODE_ENV=production
```

## 🔍 Post-Deployment Checklist

- [ ] Application loads correctly
- [ ] User registration works
- [ ] User login works
- [ ] AI chat functionality works
- [ ] Database connections are stable
- [ ] SSL certificate is valid
- [ ] Environment variables are set
- [ ] Error monitoring is configured
- [ ] Backup strategy is in place

## 📊 Monitoring

### Recommended Tools
- **Vercel Analytics** - For Vercel deployments
- **Sentry** - Error tracking
- **LogRocket** - Session recording
- **Uptime Robot** - Uptime monitoring

## 🔄 CI/CD Pipeline

### GitHub Actions Example
Create `.github/workflows/deploy.yml`:

```yaml
name: Deploy to Production

on:
  push:
    branches: [main]

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      
      - name: Setup Node.js
        uses: actions/setup-node@v3
        with:
          node-version: 18
          
      - name: Install dependencies
        run: npm ci
        
      - name: Run tests
        run: npm test
        
      - name: Build application
        run: npm run build
        
      - name: Deploy to Vercel
        uses: amondnet/vercel-action@v20
        with:
          vercel-token: ${{ secrets.VERCEL_TOKEN }}
          vercel-org-id: ${{ secrets.ORG_ID }}
          vercel-project-id: ${{ secrets.PROJECT_ID }}
```

## 🛠️ Troubleshooting

### Common Issues
1. **Build Failures** - Check environment variables
2. **Database Connection** - Verify DATABASE_URL
3. **API Keys** - Ensure all keys are valid
4. **CORS Issues** - Check NEXTAUTH_URL setting

### Performance Optimization
- Enable compression in Nginx
- Use CDN for static assets
- Implement caching strategies
- Monitor database performance

## 📞 Support

If you encounter deployment issues:
1. Check the deployment logs
2. Verify all environment variables
3. Test locally first
4. Create an issue on GitHub

---

**Happy Deploying! 🚀**
