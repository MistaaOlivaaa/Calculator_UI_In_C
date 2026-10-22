# 🧮 Calculator by MISTAAAOLIVAA

![Screenshot from 2025-07-02 06-43-24](https://github.com/user-attachments/assets/e6495c1a-3c08-451f-8b6d-a24a27feb2ef)

*Modern GTK3 calculator interface*

A lightweight calculator written in C with a GTK3 graphical interface. The project
can be built locally on Linux or run on Windows through Docker and an X11 server.

![Calculator Demo](https://img.shields.io/badge/Status-Ready%20to%20Use-brightgreen)
![Platform](https://img.shields.io/badge/Platform-Linux%20%7C%20Windows-blue)
![Language](https://img.shields.io/badge/Language-C-orange)

## ✨ Features

- Clean, modern GTK3 interface
- Basic arithmetic operations: `+`, `-`, `*`, `/`
- Decimal number support
- Clear function for fresh calculations
- Lightweight C application
- Linux build and Windows Docker workflow

## 📁 Project structure

```text
Calculator_UI_In_C/
├── src/
│   ├── calculator.c       # Calculator source code
│   └── Dockerfile         # Docker image definition
├── windows_setup/
│   ├── setup.bat          # Guided Windows setup
│   ├── run_calculator.bat # Build and launch helper
│   └── install_docker.ps1 # Docker, WSL2 and VcXsrv setup helper
├── CMakeLists.txt         # CMake build configuration
├── .dockerignore          # Docker build exclusions
└── README.md              # Project documentation
```

## 🚀 Quick start

### Linux 🐧

Install GTK3 development files, CMake and a C compiler. On Ubuntu or Debian:

```bash
sudo apt-get update
sudo apt-get install build-essential cmake pkg-config libgtk-3-dev
```

Build the project from the repository root:

```bash
mkdir -p build
cd build
cmake ..
cmake --build .
./calculator
```

### Windows 🪟

The Windows workflow uses Docker Desktop to build the GTK3 application and an X11
server such as VcXsrv to display the graphical window.

#### Option 1: Guided setup

1. Right-click `windows_setup/setup.bat` and run it as administrator.
2. Restart Windows if WSL2 or Docker Desktop requests it.
3. Start Docker Desktop.
4. Start VcXsrv (XLaunch) with display number `0` and allow connections from
   other hosts.
5. From the repository root, run `windows_setup/run_calculator.bat`.

#### Option 2: Manual setup

Install the following tools:

- [Docker Desktop](https://www.docker.com/products/docker-desktop/)
- [WSL2](https://learn.microsoft.com/en-us/windows/wsl/install)
- [VcXsrv](https://sourceforge.net/projects/vcxsrv/)

The setup helper can also be launched from an elevated PowerShell window:

```powershell
powershell -ExecutionPolicy Bypass -File ".\windows_setup\install_docker.ps1"
```

After Docker Desktop and VcXsrv are running, build and start the calculator from
the repository root:

```powershell
docker build -t calculator -f .\src\Dockerfile .
docker run -e DISPLAY=host.docker.internal:0.0 --rm calculator
```

> **Note:** The Docker image uses `host.docker.internal:0.0` to connect to the
> X11 server running on Windows. If the window does not appear, check that
> VcXsrv is running and that its access-control setting allows Docker
> connections.

## 🎯 How to use

- Click the number buttons to enter a value.
- Use `+`, `-`, `*` or `/` to select an operation.
- Click `.` to enter decimal values.
- Click `C` to clear the current calculation.
- Click `=` to display the result.

## 🔧 Troubleshooting

### Linux

- **GTK3 not found:** install `libgtk-3-dev` and `pkg-config`.
- **CMake not found:** install `cmake`.
- **Build directory already exists:** remove its contents or use another
  directory, then run `cmake ..` again.

### Windows

- **Docker is not running:** start Docker Desktop and wait until it is ready.
- **The calculator window does not appear:** start VcXsrv, use display `0`, and
  allow connections from other hosts.
- **The setup script fails:** run PowerShell as administrator and ensure WSL2 is
  available.
- **The Docker build cannot find files:** run the commands from the repository
  root and keep the `src/` directory in place.

## 🤝 Contributing

1. Fork the repository.
2. Create a feature branch.
3. Make your changes.
4. Test the application on the affected platform(s).
5. Open a pull request.

## 🙏 Acknowledgments

- [GTK3](https://www.gtk.org/) for the graphical interface
- Docker for the Windows build environment
- The open-source community



