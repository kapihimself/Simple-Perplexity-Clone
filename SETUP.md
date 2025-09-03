# 🛠️ Setup Guide

This guide will help you set up the AI Assistant (Perplexity Clone) project step by step.

## 📋 Prerequisites

Before you begin, ensure you have the following installed:

- **Node.js 18+** - [Download here](https://nodejs.org/)
- **npm** or **yarn** - Comes with Node.js
- **Git** - [Download here](https://git-scm.com/)

## 🔧 Installation Steps

### 1. Clone the Repository
```bash
git clone https://github.com/yourusername/perplexity-clone.git
cd perplexity-clone
```

### 2. Install Dependencies
```bash
npm install
```

### 3. Environment Configuration

Create a `.env.local` file in the root directory with the following content:

```env
# Database Configuration
DATABASE_URL="file:./dev.db"

# NextAuth.js Configuration
NEXTAUTH_URL="http://localhost:3000"
NEXTAUTH_SECRET="your-nextauth-secret-key-here"

# OpenAI API Configuration
OPENAI_API_KEY="sk-proj-your-openai-api-key-here"

# Google Gemini API Configuration  
GEMINI_API_KEY="AIza-your-gemini-api-key-here"

# Midtrans Payment Gateway Configuration (Optional)
MIDTRANS_MERCHANT_ID="your-merchant-id"
MIDTRANS_CLIENT_KEY="Mid-client-your-client-key"
MIDTRANS_SERVER_KEY="Mid-server-your-server-key"
MIDTRANS_IS_PRODUCTION="false"
```

### 4. Generate NextAuth Secret
Run this command to generate a secure secret:
```bash
openssl rand -base64 32
```
Copy the output and paste it as your `NEXTAUTH_SECRET` value.

### 5. Get API Keys

#### OpenAI API Key
1. Go to [OpenAI Platform](https://platform.openai.com/)
2. Sign up or log in
3. Navigate to "API Keys" section
4. Click "Create new secret key"
5. Copy the key and add it to your `.env.local`

#### Google Gemini API Key
1. Go to [Google AI Studio](https://makersuite.google.com/)
2. Sign in with your Google account
3. Click "Get API Key"
4. Create a new project if needed
5. Copy the key and add it to your `.env.local`

#### Midtrans Keys (Optional - for payment features)
1. Go to [Midtrans Dashboard](https://dashboard.midtrans.com/)
2. Register for a merchant account
3. Go to Settings > Access Keys
4. Copy the Server Key and Client Key
5. Add them to your `.env.local`

### 6. Database Setup
```bash
# Initialize the database
npx prisma db push

# Generate Prisma client
npx prisma generate
```

### 7. Start Development Server
```bash
npm run dev
```

The application will be available at `http://localhost:3000` (or another port if 3000 is occupied).

## 🎯 First Time Setup Checklist

- [ ] Node.js 18+ installed
- [ ] Repository cloned
- [ ] Dependencies installed (`npm install`)
- [ ] `.env.local` file created
- [ ] NextAuth secret generated
- [ ] OpenAI API key added
- [ ] Gemini API key added
- [ ] Database initialized (`npx prisma db push`)
- [ ] Development server running (`npm run dev`)

## 🔍 Troubleshooting

### Port Already in Use
If port 3000 is already in use, Next.js will automatically use the next available port (e.g., 3001).

### Database Issues
If you encounter database issues:
```bash
# Reset the database
rm dev.db
npx prisma db push
```

### API Key Issues
- Ensure your OpenAI API key starts with `sk-proj-`
- Ensure your Gemini API key starts with `AIza`
- Check that keys are properly set in `.env.local`

### Environment Variables Not Loading
- Make sure `.env.local` is in the root directory
- Restart the development server after changing environment variables
- Ensure there are no spaces around the `=` sign in your `.env.local`

## 🚀 Next Steps

Once setup is complete:

1. **Create an Account** - Go to `/register` and create a user account
2. **Test Login** - Try logging in with your credentials
3. **Try the Chat** - Access `/dashboard` and start chatting with AI
4. **Explore Features** - Check out settings, billing, and other features

## 📞 Need Help?

If you encounter issues:

1. Check the console for error messages
2. Verify all environment variables are set correctly
3. Ensure all dependencies are installed
4. Check the GitHub Issues page for common problems
5. Create a new issue if your problem isn't listed

## 🔄 Development Workflow

For ongoing development:

```bash
# Start development server
npm run dev

# Run linting
npm run lint

# Build for production
npm run build

# Start production server
npm run start
```

## 📊 Database Management

### View Database
```bash
# Open Prisma Studio to view/edit data
npx prisma studio
```

### Reset Database
```bash
# Clear all data and reset schema
rm dev.db
npx prisma db push
```

### Backup Database
```bash
# Create a backup of your SQLite database
cp dev.db dev.db.backup
```
