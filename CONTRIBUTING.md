# Contributing to Power Platform Skill

Thank you for your interest in contributing! We welcome contributions from everyone in the community.

## 📋 Ways to Contribute

### 1. Report Bugs
Found an issue? [Open a GitHub issue](https://github.com/yourusername/power-platform-skill/issues/new) with:
- Clear description of the bug
- Steps to reproduce
- Expected vs actual behavior
- Screenshots if applicable

### 2. Suggest Improvements
Have an idea? [Start a discussion](https://github.com/yourusername/power-platform-skill/discussions) or open an issue with:
- Clear description of the improvement
- Why it would be helpful
- Example use cases
- Mockups or wireframes if applicable

### 3. Add Documentation
Help improve documentation by:
- Fixing typos or unclear sections
- Adding examples or use cases
- Improving existing guides
- Adding missing documentation

### 4. Contribute Code
Help with:
- Bug fixes
- New features
- Performance improvements
- Code quality enhancements

### 5. Share Examples
Share your real-world examples:
- Custom workflows
- Integration patterns
- Best practices
- Lessons learned

---

## 🚀 Getting Started

### Fork the Repository
```bash
# Fork on GitHub, then clone locally
git clone https://github.com/yourusername/power-platform-skill.git
cd power-platform-skill
```

### Create a Branch
```bash
# Create feature branch
git checkout -b feature/your-feature-name

# Or for bug fixes
git checkout -b fix/bug-description
```

### Make Changes
1. **For documentation**: Edit markdown files directly
2. **For code**: Follow Python style guidelines (PEP 8)
3. **For examples**: Test thoroughly before submitting

### Commit Changes
```bash
git add .
git commit -m "Clear, descriptive commit message"
```

Follow these commit message guidelines:
- Start with action verb: "Add", "Fix", "Update", "Remove"
- Be specific and clear
- Reference issues if applicable: "Fixes #123"

### Push and Create Pull Request
```bash
git push origin feature/your-feature-name
```

Then create a Pull Request on GitHub with:
- Clear title describing the change
- Description of what changed and why
- Link to related issues
- Screenshots for UI changes

---

## 📝 Code Style Guidelines

### Python Code
- Follow [PEP 8](https://www.python.org/dev/peps/pep-0008/)
- Use descriptive variable names
- Add docstrings to functions
- Include type hints where possible
- Write clear comments for complex logic

### Markdown Documentation
- Use clear, concise language
- Add headers for organization
- Include code examples where relevant
- Use tables for comparisons
- Add links to related documentation

### Naming Conventions
- Files: `lowercase_with_underscores.md`
- Functions: `lowercase_with_underscores()`
- Classes: `PascalCase`
- Constants: `UPPERCASE_WITH_UNDERSCORES`

---

## 🔍 Review Process

### Before Submitting
- [ ] Changes follow style guidelines
- [ ] Code/docs are tested
- [ ] Commit messages are clear
- [ ] No unnecessary files included
- [ ] Documentation is updated

### During Review
- We may ask for changes or clarifications
- Feedback is constructive and friendly
- We appreciate your patience while reviewing
- Feel free to ask questions

### After Approval
- Changes are merged to main branch
- You'll be credited in release notes
- Your contribution helps the community!

---

## 📚 Development Setup

### For Documentation Changes
No special setup needed! Just edit markdown files.

### For Code Changes
```bash
# Create virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies (if any)
pip install -r requirements-dev.txt

# Run tests (if available)
python -m pytest

# Validate your changes
python scripts/validate.py
```

---

## 🎯 What We're Looking For

### High Priority
- Bug fixes (especially security-related)
- Documentation improvements
- Additional D365 FO patterns and examples
- Integration scenario guidance
- Troubleshooting guides

### Medium Priority
- Performance improvements
- Code refactoring
- Additional examples
- Alternative installation methods
- Translated versions

### Nice to Have
- UI/Design improvements
- Video tutorials
- Community examples
- Tool integrations

---

## 📖 Documentation Standards

### Skill Documentation
- Clear, step-by-step instructions
- Real-world examples
- Common pitfalls and how to avoid them
- Links to related content
- Screenshots/diagrams where helpful

### Code Comments
```python
# Good: Explains WHY, not WHAT
# Check if deployment environment exists before proceeding
if environment_exists:

# Bad: States obvious facts
# Set variable to true
is_valid = True
```

### Commit Messages
```
Good:
  "Add D365 FO extension pattern guide"
  "Fix bug in installation validation script"
  "Update security roles documentation with team examples"

Bad:
  "Update stuff"
  "Fix things"
  "Changes"
```

---

## 🤝 Community Guidelines

### Be Respectful
- Treat everyone with respect
- No harassment, discrimination, or hate speech
- Disagreements are OK; personal attacks are not
- Assume good intentions

### Be Constructive
- Provide helpful feedback
- Suggest improvements, not just criticism
- Share knowledge generously
- Help newer contributors

### Be Inclusive
- Welcome people from all backgrounds
- Help people learn and grow
- Explain technical concepts clearly
- Include everyone in discussions

---

## 🔐 Security

### Reporting Security Issues
If you discover a security vulnerability:
1. **DO NOT** open a public issue
2. **DO** email security@example.com with details
3. Include steps to reproduce if possible
4. We'll respond within 48 hours

### Security Best Practices
- Never commit passwords or secrets
- Use .gitignore for sensitive files
- Review code changes for security issues
- Keep dependencies updated

---

## 📞 Getting Help

### Questions?
- [GitHub Discussions](https://github.com/yourusername/power-platform-skill/discussions)
- [Open an issue](https://github.com/yourusername/power-platform-skill/issues)
- [Email us](mailto:contact@example.com)

### Resources
- [README.md](README.md) - Overview
- [Installation Guide](docs/INSTALLATION.md) - How to install
- [Quick Start](docs/QUICK_START.md) - 5-minute guide
- [Visual Guide](docs/SKILL_VISUAL_GUIDE_WITH_DIAGRAMS.md) - How it works

---

## 📋 Pull Request Checklist

Before submitting a PR, verify:
- [ ] Branch is up to date with main
- [ ] Changes are focused and specific
- [ ] Tests pass (if applicable)
- [ ] Documentation is updated
- [ ] Commit messages are clear
- [ ] No unrelated changes included
- [ ] No sensitive data in code
- [ ] Code follows style guidelines

---

## 🎉 Thank You!

Your contributions help make this skill better for everyone. We appreciate your time and effort!

### Contribution Types We Value
- ⭐ Bug reports with clear reproduction steps
- ⭐ Documentation improvements and clarifications
- ⭐ Real-world examples and use cases
- ⭐ Additional workflow guidance
- ⭐ Community support and mentoring
- ⭐ Code quality improvements

---

## 📝 License

By contributing, you agree that your contributions will be licensed under the MIT License.

---

## Questions?

Don't hesitate to ask! Contributing should be fun and rewarding. We're here to help!

- [GitHub Issues](https://github.com/yourusername/power-platform-skill/issues)
- [GitHub Discussions](https://github.com/yourusername/power-platform-skill/discussions)
- [Email](mailto:contact@example.com)

Thank you for being part of our community! 🚀
