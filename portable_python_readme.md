# Python UV Template (Always Portable) 🚀

[![Python 3.12](https://img.shields.io/badge/python-3.12-blue.svg)](https://www.python.org/downloads/)
[![UV](https://img.shields.io/badge/uv-enabled-blue)](https://github.com/astral-sh/uv)
[![Portable](https://img.shields.io/badge/portable-100%25-green)](https://github.com/indygreg/python-build-standalone)

A professional Python project template that **always uses portable Python** - never relies on system installations.

## ✨ Philosophy

- 🎯 **Always Portable** - Consistent Python environment everywhere
- 📦 **Self-Contained** - No dependency on system Python
- 🔄 **Reproducible** - Same exact Python version every time
- 🚀 **Distributable** - Package includes everything needed

## 🚀 Quick Start

```bash
# 1. Clone or use this template
git clone https://github.com/yourusername/your-project
cd your-project

# 2. Run setup (downloads Python 3.12.7 first time, ~2 minutes)
./setup-portable.sh

# 3. Activate and run
source .venv/bin/activate
python src/main.py
```

That's it! No system Python needed.

## 📁 What Gets Created

```
your-project/
├── .python/              # Portable Python 3.12.7 (~80MB)
├── .venv/                # Virtual environment with dependencies
├── src/
│   └── main.py
├── setup-portable.sh     # Setup script
└── pyproject.toml
```

## 🎯 Common Commands

```bash
# Setup (first time downloads Python, subsequent runs reuse it)
./setup-portable.sh

# If something breaks, clean rebuild
./setup-portable.sh --force-clean

# Add a dependency
# 1. Edit pyproject.toml
# 2. Then:
uv lock
uv sync

# Create distributable package
./package-portable.sh
```

## 📦 Creating Packages

```bash
# Create self-contained package
./package-portable.sh

# Result: dist/my-app-1.0.0-portable.tar.gz (~50MB compressed)

# To run on another machine (no Python needed!):
tar -xzf my-app-1.0.0-portable.tar.gz
cd my-app-1.0.0-portable
./run.sh
```

## 🔧 How It Works

### First Time

1. Downloads pre-built Python 3.12.7 from [python-build-standalone](https://github.com/indygreg/python-build-standalone)
2. Installs to `.python/` directory
3. Creates virtual environment in `.venv/`
4. Installs dependencies with UV

### Subsequent Runs

1. Finds existing `.python/` installation
2. Reuses it (no download needed!)
3. Creates fresh `.venv/`
4. Installs dependencies

### With `--force-clean`

1. Deletes `.python/`, `.venv/`, `uv.lock`
2. Downloads Python again
3. Fresh installation

## 💡 Why Portable Python?

| System Python | Portable Python |
|---------------|-----------------|
| ❌ Different versions on different machines | ✅ Exact same version everywhere |
| ❌ Might not be installed | ✅ Always available |
| ❌ User might update it | ✅ Controlled version |
| ❌ Dependency conflicts | ✅ Self-contained |
| ❌ "Works on my machine" | ✅ Works everywhere |

## 📊 Disk Space

- `.python/` : ~80 MB (one-time)
- `.venv/` : ~50 MB (varies by dependencies)
- **Total**: ~150 MB uncompressed
- **Package**: ~50 MB compressed

Small price for complete portability!

## 🛠️ Development Workflow

```bash
# Day 1: Setup
./setup-portable.sh
source .venv/bin/activate

# Daily development
python src/main.py
pytest

# Add dependencies
# Edit pyproject.toml, then:
uv lock && uv sync

# If weird issues
./setup-portable.sh --force-clean
```

## 📮 Distribution Workflow

```bash
# 1. Ensure clean build
./setup-portable.sh --force-clean

# 2. Test your app
source .venv/bin/activate
python src/main.py

# 3. Create package
./package-portable.sh

# 4. Share dist/my-app-1.0.0-portable.tar.gz
# Users don't need Python installed!
```

## 🎨 Customization

### Change Python Version

Edit `setup-portable.sh`:
```bash
PYTHON_VERSION="3.13.0"  # Or any version
```

Available versions: https://github.com/indygreg/python-build-standalone/releases

### Configure Package

Edit `package-portable.sh`:
```bash
APP_NAME="my-app"
VERSION="1.0.0"
```

## 🐛 Troubleshooting

```bash
# Virtual environment issues
rm -rf .venv/ && ./setup-portable.sh

# Complete fresh start
./setup-portable.sh --force-clean

# Check what you have
.python/bin/python3 --version
source .venv/bin/activate && python --version
```

## 📚 Documentation

- [Setup Guide](SETUP_GUIDE.md) - Detailed guide
- [Quick Reference](QUICK_REFERENCE.md) - Command cheat sheet
- [UV Documentation](https://github.com/astral-sh/uv)

## ⚠️ Platform Compatibility

Portable Python is **OS and architecture specific**:

- ✅ macOS x86_64 → macOS x86_64
- ✅ macOS arm64 (M1/M2/M3) → macOS arm64
- ✅ Linux x86_64 → Linux x86_64
- ✅ Linux aarch64 → Linux aarch64
- ❌ macOS → Linux (use Docker)
- ❌ x86_64 → arm64 (use Docker)
- ❌ Windows (use WSL or Docker)

For cross-platform distribution, use Docker instead.

## 🐳 Docker Alternative

If you need cross-platform support, use the included Dockerfile:

```bash
# Build image
docker build -t my-app .

# Run
docker run my-app

# Distribute
docker save my-app > my-app.tar
```

## 🤝 Contributing

1. Fork the repository
2. Create feature branch (`git checkout -b feature/amazing`)
3. Make your changes
4. Run tests (`pytest`)
5. Commit (`git commit -m 'Add amazing feature'`)
6. Push (`git push origin feature/amazing`)
7. Open Pull Request

## 📄 License

MIT License - See [LICENSE](LICENSE) file

## 🙏 Acknowledgments

- [python-build-standalone](https://github.com/indygreg/python-build-standalone) - Pre-built Python distributions
- [UV](https://github.com/astral-sh/uv) - Fast Python package installer
- Built with modern Python best practices

## 📧 Support

- 📖 [Documentation](SETUP_GUIDE.md)
- 🐛 [Issues](https://github.com/yourusername/python-uv-template/issues)
- 💬 [Discussions](https://github.com/yourusername/python-uv-template/discussions)

---

⭐ If you find this template helpful, please star it!

**Ready to use?** Click "Use this template" above or clone and start building!