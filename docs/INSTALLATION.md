# Installation Guide

This guide covers 4 different ways to install the Power Platform & Dynamics 365 Management Skill.

---

## 🚀 Quick Start

Choose your preferred installation method:

| Method | Time | Best For | Requirements |
|--------|------|----------|--------------|
| **Automated** | 2-3 min | Most users | Python 3.8+ |
| **Manual** | 5 min | Simple setup | Just copy-paste |
| **Docker** | 5-10 min | Docker users | Docker installed |
| **Development** | 10 min | Contributors | Python, Git |

---

## Method 1: Automated Installation (Recommended)

Fastest and easiest way to install. Includes validation and verification.

### Requirements
- Python 3.8 or higher
- Terminal/Command Prompt
- Internet connection (for verification)

### Steps

1. **Download the installer**
   ```bash
   wget https://github.com/yourusername/power-platform-skill/raw/main/scripts/install.py
   ```
   Or if wget is not available, download from the repository.

2. **Run the installer**
   ```bash
   python install.py
   ```

3. **Follow the prompts**
   - Confirm installation location
   - Enter your organization details (optional)
   - Wait for installation to complete

4. **Verify installation**
   ```bash
   python validate.py
   ```
   You should see: ✅ Installation verified successfully

### What Gets Installed

```
~/.claude-skills/power-platform/
├── skill/
│   ├── SKILL.md
│   ├── QUICK_REFERENCE.md
│   └── references/
│       ├── d365-fo-development.md
│       ├── data-operations.md
│       ├── entity-management.md
│       ├── integrations.md
│       └── security-roles.md
├── docs/
│   └── [all documentation]
└── preferences.yaml
```

### Troubleshooting Automated Install

**Issue:** Python not found
- **Solution:** Install Python 3.8+ from [python.org](https://www.python.org)
- **Test:** Run `python --version`

**Issue:** Permission denied
- **Solution (macOS/Linux):** Run `chmod +x install.py` first
- **Solution (Windows):** Run Command Prompt as Administrator

**Issue:** Installation path error
- **Solution:** Check that `~/.claude-skills/` directory is writable
- **Test:** Run `python validate.py` to verify installation

---

## Method 2: Manual Installation

Simple copy-paste method. No dependencies required.

### Requirements
- Web browser (to download files)
- File manager or terminal
- 5 minutes of time

### Steps

1. **Create the directory**
   ```bash
   mkdir -p ~/.claude-skills/power-platform/skill/references
   mkdir -p ~/.claude-skills/power-platform/docs
   ```

2. **Download the files**
   - Go to GitHub repository
   - Click "Code" → "Download ZIP"
   - Extract the ZIP file

3. **Copy skill files**
   ```bash
   # Copy main skill files
   cp skill/SKILL.md ~/.claude-skills/power-platform/skill/
   cp skill/QUICK_REFERENCE.md ~/.claude-skills/power-platform/skill/
   
   # Copy reference guides
   cp skill/references/* ~/.claude-skills/power-platform/skill/references/
   
   # Copy documentation
   cp docs/* ~/.claude-skills/power-platform/docs/
   ```

4. **Create preferences file (optional)**
   ```bash
   cat > ~/.claude-skills/power-platform/preferences.yaml << 'EOF'
   organization: "Your Organization"
   version_format: "1.0.YYYYMM"
   user_role: "Admin"  # or Developer, Manager, Power User
   EOF
   ```

5. **Verify installation**
   ```bash
   ls ~/.claude-skills/power-platform/skill/
   ```
   Should show: SKILL.md, QUICK_REFERENCE.md, references/

### Windows Users

If you're on Windows, the path would be:
```
C:\Users\YourUsername\.claude-skills\power-platform\
```

Use File Explorer:
1. Open `C:\Users\YourUsername`
2. Create folder: `.claude-skills\power-platform\skill\references`
3. Copy files using drag-and-drop

---

## Method 3: Docker Installation

Best for isolated environments and reproducible setups.

### Requirements
- Docker installed and running
- Terminal/Command Prompt
- ~500MB disk space

### Steps

1. **Clone the repository**
   ```bash
   git clone https://github.com/yourusername/power-platform-skill.git
   cd power-platform-skill
   ```

2. **Build the Docker image**
   ```bash
   docker build -t power-platform-skill:latest .
   ```

3. **Run the container**
   ```bash
   docker run -it --name power-skill-setup power-platform-skill:latest
   ```

4. **Copy files from container (optional)**
   ```bash
   docker cp power-skill-setup:/app/skill ~/.claude-skills/power-platform/
   ```

5. **Verify installation**
   ```bash
   docker run power-platform-skill:latest python validate.py
   ```

### Docker Troubleshooting

**Issue:** Docker daemon not running
- **Solution:** Start Docker Desktop or Docker daemon

**Issue:** Permission denied
- **Solution (Linux):** Add user to docker group: `sudo usermod -aG docker $USER`

**Issue:** Image build fails
- **Solution:** Check internet connection and disk space

---

## Method 4: Development Installation

For contributors who want to modify the skill.

### Requirements
- Python 3.8+
- Git
- Text editor (VS Code recommended)
- Terminal experience

### Steps

1. **Fork and clone**
   ```bash
   # Fork on GitHub first, then:
   git clone https://github.com/yourusername/power-platform-skill.git
   cd power-platform-skill
   ```

2. **Create virtual environment**
   ```bash
   python -m venv venv
   
   # Activate (macOS/Linux)
   source venv/bin/activate
   
   # Activate (Windows)
   venv\Scripts\activate
   ```

3. **Install development dependencies**
   ```bash
   pip install -r requirements-dev.txt
   ```

4. **Run validation**
   ```bash
   python scripts/validate.py --verbose
   ```

5. **Make changes and test**
   - Edit files in the `skill/` directory
   - Run validation frequently
   - Commit changes with clear messages

6. **Create pull request**
   - Push to your fork
   - Create pull request on GitHub
   - Wait for review and feedback

### Development Workflow

```bash
# Create feature branch
git checkout -b feature/add-new-guide

# Make changes
# ... edit files ...

# Validate changes
python scripts/validate.py

# Commit changes
git add .
git commit -m "Add new D365 FO guide"

# Push to GitHub
git push origin feature/add-new-guide

# Create pull request on GitHub
```

---

## ✅ Verification Steps

After installation, verify everything works:

### Quick Verification
```bash
# Check main skill file exists
ls ~/.claude-skills/power-platform/skill/SKILL.md

# Check references exist
ls ~/.claude-skills/power-platform/skill/references/

# Check documentation exists
ls ~/.claude-skills/power-platform/docs/
```

### Detailed Verification

Run the validation script:
```bash
python validate.py
```

Expected output:
```
✅ Directory structure verified
✅ SKILL.md found
✅ Reference files found (5)
✅ Documentation files found
✅ Preferences file found
✅ Installation verified successfully
```

### In Claude

1. Copy your skill file content
2. In Claude, paste or import the skill
3. Ask: "How do I deploy a solution?"
4. Should get step-by-step deployment guidance

---

## 🔧 Post-Installation Configuration

### Create Your Preferences

After installation, customize your preferences:

```bash
cat > ~/.claude-skills/power-platform/preferences.yaml << 'EOF'
organization: "Acme Corporation"
version_format: "1.0.YYYYMM"  # or MAJOR.MINOR.PATCH
user_role: "Admin"  # Admin, Developer, Manager, Power User
environments:
  - name: "Dev"
    type: "Sandbox"
  - name: "Test"
    type: "Sandbox"
  - name: "PreProd"
    type: "Sandbox"
  - name: "Prod"
    type: "Production"
EOF
```

### Using in Claude.ai

1. Go to Claude.ai
2. Open the chat interface
3. In your message, reference or paste the skill file
4. Ask questions about Power Platform tasks
5. Get personalized guidance based on your role

---

## 📊 Installation Paths by Operating System

### macOS
```
~/.claude-skills/power-platform/
```

### Linux
```
~/.claude-skills/power-platform/
```
or if using snap:
```
~/snap/power-platform-skill/common/.claude-skills/
```

### Windows
```
C:\Users\YourUsername\.claude-skills\power-platform\
```

---

## 🆘 Troubleshooting

### Installation Issues

**Problem:** "Python not found"
- Check Python is installed: `python --version`
- Install from [python.org](https://www.python.org)
- On Windows, add Python to PATH

**Problem:** "Permission denied"
- macOS/Linux: Run `chmod +x install.py`
- Windows: Run as Administrator
- Check folder permissions

**Problem:** "No space left on device"
- Check available disk space: `df -h`
- Free up space and try again
- Skill requires ~50MB

**Problem:** "Validation fails"
- Run with verbose: `python validate.py --verbose`
- Check all files copied correctly
- Reinstall using automated method

### Runtime Issues

**Problem:** "Skill not found in Claude"
- Verify installation: `ls ~/.claude-skills/power-platform/`
- Copy skill file content into Claude
- Make sure you're pasting into message body

**Problem:** "Getting generic responses"
- Check preferences.yaml exists
- Verify your role is set correctly
- Copy full SKILL.md into Claude, not just portions

**Problem:** "Diagrams not displaying"
- Diagrams are ASCII-based, should display in any environment
- If not showing, copy-paste the markdown file directly

---

## 📞 Getting Help

### If Installation Fails

1. **Check requirements**
   - Python version: `python --version` (should be 3.8+)
   - Disk space: `df -h` (need ~100MB free)
   - Permissions: Can you write to home directory?

2. **Run validation**
   ```bash
   python validate.py --verbose
   ```
   Shows detailed error messages

3. **Check GitHub Issues**
   - [GitHub Issues](https://github.com/yourusername/power-platform-skill/issues)
   - Search existing issues for your problem
   - Create new issue if not found

4. **Ask for Help**
   - [GitHub Discussions](https://github.com/yourusername/power-platform-skill/discussions)
   - [Email Support](mailto:contact@example.com)

---

## ✨ Next Steps

After successful installation:

1. **Read Quick Start**
   - See: [QUICK_START.md](QUICK_START.md)
   - Takes 5 minutes
   - Shows basic usage

2. **Check Quick Reference**
   - See: [QUICK_REFERENCE.md](../skill/QUICK_REFERENCE.md)
   - One-page lookup table
   - Find your task quickly

3. **Review Visual Guide**
   - See: [SKILL_VISUAL_GUIDE_WITH_DIAGRAMS.md](SKILL_VISUAL_GUIDE_WITH_DIAGRAMS.md)
   - Learn how skill works
   - Understand user journeys

4. **Start Using**
   - Import skill into Claude
   - Ask about your first task
   - Get step-by-step guidance

---

## 🎉 You're Ready!

Your skill is now installed and ready to use. Start with a simple question about your Power Platform or D365 task and watch the skill guide you through it!

### Quick Command Reference

```bash
# Check installation
ls ~/.claude-skills/power-platform/skill/

# Validate installation
python validate.py

# View quick reference
cat ~/.claude-skills/power-platform/skill/QUICK_REFERENCE.md

# Edit preferences
nano ~/.claude-skills/power-platform/preferences.yaml
```

---

## 📚 More Information

- [README](../README.md) - Project overview
- [Quick Start](QUICK_START.md) - 5-minute guide
- [FAQ](FAQ.md) - Common questions
- [Contributing](../CONTRIBUTING.md) - How to help
- [Visual Guide](SKILL_VISUAL_GUIDE_WITH_DIAGRAMS.md) - How it works

---

**Installation complete! 🎉 You're ready to supercharge your Dynamics 365 work!**
