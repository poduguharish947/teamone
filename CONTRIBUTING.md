# Contributing to Course Management System

Thank you for your interest in contributing to the Course Management System! This document provides guidelines and instructions for contributing.

## 🤝 How to Contribute

### Reporting Bugs

If you find a bug, please create an issue with:
- Clear title and description
- Steps to reproduce
- Expected vs actual behavior
- Screenshots if applicable
- Your environment (OS, browser, Node version)

### Suggesting Features

Feature suggestions are welcome! Please:
- Check if the feature already exists
- Describe the use case clearly
- Explain why it would be valuable
- Consider implementation complexity

### Pull Requests

1. **Fork the repository**
2. **Create a feature branch**: `git checkout -b feature/YourFeature`
3. **Make your changes**
4. **Test thoroughly**
5. **Commit with clear messages**: `git commit -m "Add feature: description"`
6. **Push to your fork**: `git push origin feature/YourFeature`
7. **Open a Pull Request**

## 📋 Development Guidelines

### Code Style

**JavaScript**:
- Use meaningful variable names
- Add comments for complex logic
- Follow existing code patterns
- Use async/await for asynchronous operations

**HTML/CSS**:
- Maintain responsive design
- Use semantic HTML5 elements
- Keep consistent indentation (2 or 4 spaces)
- Follow BEM methodology for CSS classes

### Commit Messages

Follow this format:
```
Type: Brief description

Detailed explanation if needed

- List specific changes
- Reference issues: Fixes #123
```

**Types**: 
- `feat`: New feature
- `fix`: Bug fix
- `docs`: Documentation
- `style`: Formatting
- `refactor`: Code restructuring
- `test`: Adding tests
- `chore`: Maintenance

### Testing

Before submitting:
- Test all user flows
- Check both teacher and student roles
- Verify standalone version still works
- Test on different browsers
- Check mobile responsiveness

## 🏗️ Project Structure

```
course-management-system/
├── backend/              # Node.js + Express backend
│   ├── server.js        # Main API (modify with care)
│   └── package.json     # Backend dependencies
├── Project-Modern.html  # Main entry (with backend)
├── Project-Modern-Standalone.html  # Standalone version
├── dashboard-*.js       # Frontend logic
└── docs/                # Documentation
```

## 🎯 Areas for Contribution

### High Priority
- [ ] Unit tests for backend API
- [ ] Frontend testing framework
- [ ] Accessibility improvements (ARIA labels, keyboard navigation)
- [ ] Performance optimization
- [ ] Security enhancements

### Medium Priority
- [ ] Dark mode theme
- [ ] Email notifications
- [ ] File upload improvements
- [ ] Search and filter enhancements
- [ ] Export data functionality

### Low Priority
- [ ] Internationalization (i18n)
- [ ] Mobile app version
- [ ] Advanced analytics charts
- [ ] Calendar integration
- [ ] Video conferencing integration

## 🔧 Development Setup

1. **Clone your fork**:
```bash
git clone https://github.com/YOUR_USERNAME/course-management-system.git
cd course-management-system
```

2. **Install dependencies**:
```bash
cd backend
npm install
```

3. **Set up environment**:
```bash
cp .env.example .env
# Edit .env with your MongoDB URI
```

4. **Start development**:
```bash
npm run dev
```

## 📝 Documentation

When adding features:
- Update relevant `.md` files
- Add API endpoint documentation to `backend/README.md`
- Update `COMPLETE_FEATURES_GUIDE.md` if needed
- Include usage examples

## ✅ Pull Request Checklist

Before submitting, ensure:
- [ ] Code follows project style
- [ ] All features work as expected
- [ ] Standalone version still functions
- [ ] No console errors or warnings
- [ ] Documentation updated
- [ ] Commit messages are clear
- [ ] No merge conflicts
- [ ] Tested on multiple browsers

## 🚫 What Not to Do

- Don't commit `node_modules/` or `.env` files
- Don't make breaking changes without discussion
- Don't remove existing features without reason
- Don't ignore code style guidelines
- Don't submit untested code

## 💡 Getting Help

- Review existing code and documentation
- Check closed issues for similar questions
- Open a discussion for major changes
- Ask questions in issue comments

## 📜 License

By contributing, you agree that your contributions will be licensed under the MIT License.

## 🌟 Recognition

Contributors will be:
- Listed in the project README
- Mentioned in release notes
- Appreciated in the community!

Thank you for making this project better! 🎉
