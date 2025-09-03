# 🤝 Contributing to AI Assistant (Perplexity Clone)

Thank you for considering contributing to this project! This document provides guidelines and information for contributors.

## 🌟 How to Contribute

### 1. Fork the Repository
1. Fork the project on GitHub
2. Clone your fork locally
3. Create a new branch for your feature/fix

### 2. Development Setup
Follow the [Setup Guide](SETUP.md) to get the project running locally.

### 3. Making Changes
1. Create a new branch: `git checkout -b feature/your-feature-name`
2. Make your changes
3. Test your changes thoroughly
4. Commit your changes with a clear message

### 4. Code Style
- Use TypeScript for all new code
- Follow the existing code style
- Run `npm run lint` before committing
- Use meaningful variable and function names
- Add comments for complex logic

### 5. Testing
- Test your changes manually
- Ensure all existing functionality still works
- Test on different screen sizes (mobile/desktop)
- Verify API integrations work correctly

### 6. Submitting Changes
1. Push your branch to your fork
2. Create a Pull Request
3. Provide a clear description of your changes
4. Link any relevant issues

## 🐛 Bug Reports

When filing bug reports, please include:

- **Description** - Clear description of the bug
- **Steps to Reproduce** - Detailed steps to reproduce the issue
- **Expected Behavior** - What you expected to happen
- **Actual Behavior** - What actually happened
- **Environment** - OS, browser, Node.js version
- **Screenshots** - If applicable

### Bug Report Template
```markdown
**Describe the bug**
A clear and concise description of what the bug is.

**To Reproduce**
Steps to reproduce the behavior:
1. Go to '...'
2. Click on '....'
3. Scroll down to '....'
4. See error

**Expected behavior**
A clear and concise description of what you expected to happen.

**Screenshots**
If applicable, add screenshots to help explain your problem.

**Environment:**
 - OS: [e.g. macOS, Windows, Linux]
 - Browser: [e.g. Chrome, Firefox, Safari]
 - Node.js Version: [e.g. 18.17.0]
 - Project Version: [e.g. 1.0.0]
```

## ✨ Feature Requests

For feature requests, please include:

- **Feature Description** - Clear description of the feature
- **Use Case** - Why this feature would be useful
- **Implementation Ideas** - Any thoughts on how it could be implemented
- **Alternatives** - Alternative solutions you've considered

## 📝 Code Guidelines

### TypeScript
- Use TypeScript for all new code
- Define proper interfaces and types
- Avoid `any` types when possible
- Use meaningful type names

### React Components
- Use functional components with hooks
- Follow the existing component structure
- Use proper prop types
- Keep components focused and reusable

### API Routes
- Follow RESTful conventions
- Include proper error handling
- Validate input data
- Use appropriate HTTP status codes

### Database
- Use Prisma for database operations
- Follow the existing schema patterns
- Include proper relations
- Add database constraints when appropriate

### Styling
- Use Tailwind CSS for styling
- Follow the existing design patterns
- Ensure responsive design
- Use the existing color scheme

## 🔧 Development Tools

### Required Tools
- **Node.js 18+** - Runtime environment
- **npm** - Package manager
- **Git** - Version control
- **VSCode** (recommended) - Code editor

### Recommended Extensions
- TypeScript and JavaScript Language Features
- Tailwind CSS IntelliSense
- Prisma
- ESLint
- Prettier

### Development Commands
```bash
# Start development server
npm run dev

# Run linting
npm run lint

# Build for production
npm run build

# Database operations
npx prisma studio
npx prisma db push
npx prisma generate
```

## 🚀 Areas for Contribution

### High Priority
- **AI Model Integration** - Add support for more AI providers
- **Performance Optimization** - Improve response times
- **Mobile Experience** - Enhance mobile UI/UX
- **Testing** - Add unit and integration tests
- **Documentation** - Improve existing docs

### Medium Priority
- **Internationalization** - Add multi-language support
- **Accessibility** - Improve accessibility features
- **Analytics** - Add usage analytics
- **Export Features** - Add chat export functionality
- **Themes** - Additional UI themes

### Low Priority
- **Browser Extensions** - Browser integration
- **Desktop App** - Electron wrapper
- **API Documentation** - OpenAPI specifications
- **Admin Panel** - User management interface

## 📋 Pull Request Process

1. **Branch Naming**
   - `feature/description` - For new features
   - `fix/description` - For bug fixes
   - `docs/description` - For documentation
   - `refactor/description` - For code refactoring

2. **Commit Messages**
   ```
   type(scope): description
   
   Examples:
   feat(chat): add message export functionality
   fix(auth): resolve login redirect issue
   docs(readme): update installation instructions
   ```

3. **Pull Request Title**
   - Use a clear, descriptive title
   - Reference issue numbers if applicable

4. **Pull Request Description**
   - Describe what changes were made
   - Explain why the changes were necessary
   - Include any breaking changes
   - Add screenshots for UI changes

## 🎯 Getting Started

### Good First Issues
Look for issues labeled `good first issue` or `help wanted`. These are:
- Documentation improvements
- UI/UX enhancements
- Small feature additions
- Bug fixes

### Setting Up Development Environment
1. Follow the [Setup Guide](SETUP.md)
2. Run the project locally
3. Explore the codebase
4. Try making a small change
5. Submit your first Pull Request!

## 📞 Getting Help

- **GitHub Discussions** - For general questions
- **GitHub Issues** - For bugs and feature requests
- **Code Review** - We provide helpful feedback on PRs

## 🙏 Recognition

Contributors will be:
- Listed in the project README
- Mentioned in release notes
- Invited to join the contributor team (for regular contributors)

## 📄 License

By contributing, you agree that your contributions will be licensed under the same license as the project (MIT License).

---

**Thank you for contributing to make this project better! 🎉**
