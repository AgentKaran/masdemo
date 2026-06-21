# masdemo

## Overview

`masdemo` is a lightweight demonstration project showcasing the core functionalities of the **MAS (Modular Application System)** framework. It provides example implementations of common patterns such as configuration management, logging, and modular component integration, making it an excellent starting point for new developers or a reference implementation for seasoned contributors.

## Features

- **Modular Architecture** – Demonstrates how to structure an application using MAS modules.
- **Configuration Management** – Shows loading configuration from YAML/JSON files and environment variables.
- **Logging** – Integrated, configurable logging with multiple output handlers.
- **Command‑Line Interface** – Simple CLI built with `argparse` (or `click`) for interacting with the demo.
- **Testing** – Includes a basic test suite using `pytest`.
- **Docker Support** – Dockerfile for containerised execution.

## Getting Started

### Prerequisites

- Python 3.9 or newer
- `pip` package manager
- (Optional) Docker if you want to run the containerised version

### Installation

```bash
# Clone the repository
git clone https://github.com/your-org/masdemo.git
cd masdemo

# Create a virtual environment (recommended)
python -m venv .venv
source .venv/bin/activate  # On Windows use `.venv\Scripts\activate`

# Install dependencies
pip install -r requirements.txt
```

### Running the Demo

```bash
# Run the application directly
python -m masdemo

# Or use the provided CLI entry point
masdemo --help
```

### Using Docker

```bash
# Build the Docker image
docker build -t masdemo:latest .

# Run the container
docker run --rm masdemo:latest
```

## Usage Examples

Below are a few common usage patterns:

### Example 1: Loading a Custom Configuration

```python
from masdemo.config import load_config

config = load_config('config/custom.yaml')
print(config['database']['host'])
```

### Example 2: Extending with a New Module

Create a new Python module under `masdemo/modules/` and register it in `masdemo/__init__.py`:

```python
# my_module.py
from masdemo.core import BaseModule

class MyModule(BaseModule):
    def start(self):
        print('My custom module is running!')
```

Then initialize it via the CLI:

```bash
masdemo --module my_module
```

## Contributing

Contributions are welcome! Please follow these steps:

1. **Fork the repository** and clone your fork.
2. **Create a feature branch**:
   ```bash
   git checkout -b feature/your-feature-name
   ```
3. **Make your changes** and ensure the test suite passes:
   ```bash
   pytest
   ```
4. **Commit your changes** with a clear commit message.
5. **Push** to your fork and open a **Pull Request** targeting the `main` branch.

### Code Style

- Follow **PEP 8** guidelines.
- Run `black .` and `flake8` before committing.
- Write unit tests for new functionality.

### Issue Reporting

If you encounter bugs or have feature requests, please open an issue with a clear description and, if possible, a minimal reproducible example.

## License

This project is licensed under the **MIT License** – see the [LICENSE](LICENSE) file for details.

---

*Happy coding!*