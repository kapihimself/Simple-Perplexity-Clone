# 🤖 AI Assistant - Perplexity Clone

A modern, full-featured AI chat application built with Next.js 15, featuring GPT-4 and Gemini Pro integration, user authentication, subscription management, and payment processing.

![AI Assistant](https://img.shields.io/badge/Next.js-15.5.2-black?style=for-the-badge&logo=next.js)
![TypeScript](https://img.shields.io/badge/TypeScript-5.0-blue?style=for-the-badge&logo=typescript)
![Tailwind CSS](https://img.shields.io/badge/Tailwind-4.0-06B6D4?style=for-the-badge&logo=tailwindcss)
![Prisma](https://img.shields.io/badge/Prisma-6.15.0-2D3748?style=for-the-badge&logo=prisma)

## ✨ Features

### 🤖 AI Integration
- **OpenAI GPT-4** - Advanced conversational AI
- **Google Gemini Pro** - Google's latest AI model
- **Real-time Chat** - Instant responses with streaming
- **Model Selection** - Choose between different AI models
- **Chat History** - Persistent conversation storage

### 👤 User Management
- **Authentication** - Secure login/registration with NextAuth.js
- **User Profiles** - Customizable user settings
- **Session Management** - Secure JWT-based sessions
- **Password Hashing** - Bcrypt encryption for security

### 💳 Subscription & Billing
- **Midtrans Integration** - Indonesian payment gateway
- **Multiple Plans** - Free, Basic, Pro, Enterprise tiers
- **Usage Tracking** - Monitor API calls and costs
- **Billing Dashboard** - Manage subscriptions and payments

### 🎨 Modern UI/UX
- **Responsive Design** - Mobile-first approach
- **Tailwind CSS** - Beautiful, customizable styling
- **Radix UI Components** - Accessible, high-quality components
- **Gradient Themes** - Modern visual design
- **Dark Mode Ready** - Built-in theme switching support

### 🔧 Technical Features
- **Next.js 15** - Latest React framework with App Router
- **TypeScript** - Type-safe development
- **Prisma ORM** - Type-safe database operations
- **SQLite/PostgreSQL** - Flexible database support
- **Turbopack** - Fast development builds
- **ESLint** - Code quality enforcement

## 🚀 Quick Start

### Prerequisites
- Node.js 18+ installed
- npm or yarn package manager
- Git for version control

### 1. Clone the Repository
```bash
git clone https://github.com/yourusername/perplexity-clone.git
cd perplexity-clone
```

### 2. Install Dependencies
```bash
npm install
```

### 3. Environment Setup
Copy the example environment file and configure your API keys:
```bash
cp .env.example .env.local
```

Edit `.env.local` with your API keys:
```env
# Database
DATABASE_URL="file:./dev.db"

# NextAuth.js Configuration
NEXTAUTH_URL="http://localhost:3000"
NEXTAUTH_SECRET="your-generated-secret-key"

# AI API Keys
OPENAI_API_KEY="sk-proj-your-openai-key"
GEMINI_API_KEY="AIza-your-gemini-key"

# Midtrans Payment Gateway
MIDTRANS_MERCHANT_ID="your-merchant-id"
MIDTRANS_CLIENT_KEY="Mid-client-your-client-key"
MIDTRANS_SERVER_KEY="Mid-server-your-server-key"
MIDTRANS_IS_PRODUCTION="false"
```

### 4. Database Setup
```bash
npx prisma db push
npx prisma generate
```

### 5. Run Development Server
```bash
npm run dev
```

Open [http://localhost:3000](http://localhost:3000) in your browser.

## 📖 API Keys Setup

### OpenAI API Key
1. Visit [OpenAI Platform](https://platform.openai.com/)
2. Create an account or sign in
3. Go to API Keys section
4. Create a new API key
5. Add to your `.env.local` file

### Google Gemini API Key
1. Visit [Google AI Studio](https://makersuite.google.com/)
2. Sign in with your Google account
3. Create a new API key
4. Add to your `.env.local` file

### Midtrans Configuration (Optional)
1. Visit [Midtrans Dashboard](https://dashboard.midtrans.com/)
2. Register for a merchant account
3. Get your Server Key and Client Key
4. Add to your `.env.local` file

## 🗄️ Database Schema

The application uses Prisma ORM with the following main models:

- **User** - User accounts and profiles
- **Subscription** - User subscription plans and billing
- **Conversation** - Chat conversations
- **Message** - Individual chat messages
- **Usage** - API usage tracking

## 🛡️ Security Features

- **JWT Authentication** - Secure session management
- **Password Hashing** - Bcrypt encryption
- **CSRF Protection** - Built-in security measures
- **Rate Limiting** - API usage protection
- **Input Validation** - Zod schema validation

## 📱 Pages & Routes

### Public Routes
- `/` - Landing page
- `/login` - User login
- `/register` - User registration

### Protected Routes
- `/dashboard` - Main chat interface
- `/dashboard/settings` - User settings
- `/dashboard/billing` - Subscription management

### API Routes
- `/api/auth/*` - NextAuth.js authentication
- `/api/chat` - AI chat endpoint
- `/api/user/settings` - User preferences
- `/api/subscription/*` - Billing management

## 🎨 Customization

### Styling
The application uses Tailwind CSS for styling. You can customize:
- Colors in `tailwind.config.ts`
- Custom CSS in `src/app/globals.css`
- Component styles in individual files

### AI Models
Add new AI providers by:
1. Installing the provider's SDK
2. Creating a new service in `src/lib/`
3. Adding configuration options
4. Updating the chat API endpoint

## 📦 Deployment

### Vercel (Recommended)
1. Connect your GitHub repository to Vercel
2. Add environment variables in Vercel dashboard
3. Deploy automatically on git push

### Docker
```bash
# Build Docker image
docker build -t perplexity-clone .

# Run container
docker run -p 3000:3000 perplexity-clone
```

### Manual Deployment
```bash
# Build for production
npm run build

# Start production server
npm run start
```

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- [OpenAI](https://openai.com/) for GPT-4 API
- [Google](https://ai.google.dev/) for Gemini Pro API
- [Vercel](https://vercel.com/) for Next.js framework
- [Radix UI](https://www.radix-ui.com/) for accessible components
- [Tailwind CSS](https://tailwindcss.com/) for styling framework

## 📞 Support

If you have any questions or need help:

1. Check the [Issues](https://github.com/yourusername/perplexity-clone/issues) page
2. Create a new issue if your problem isn't already listed
3. For urgent matters, contact the maintainers

## 🔄 Changelog

### v1.0.0 (Initial Release)
- ✅ OpenAI GPT-4 integration
- ✅ Google Gemini Pro integration
- ✅ User authentication system
- ✅ Subscription management
- ✅ Midtrans payment integration
- ✅ Modern responsive UI
- ✅ Real-time chat interface
- ✅ Database integration with Prisma

---

**Made with ❤️ using Next.js 15 and modern web technologies**