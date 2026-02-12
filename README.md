# Pentora (v1.0)

Pentora is a terminal-first web vulnerability scanner designed for speed and verified exploitation.

## 🚀 Installation (Linux/macOS/Windows)

### Prerequisites
- **Go (Golang)**: v1.21 or higher. [Install Go](https://go.dev/doc/install)

### Steps

1. **Clone the repository** (or copy the project files):
   ```bash
   git clone https://github.com/pentora/pentora.git
   cd pentora
   ```

2. **Install dependencies**:
   ```bash
   go mod tidy
   ```

3. **Build the binary**:
   ```bash
   # On Linux/macOS
   go build -o pentora cmd/pentora/main.go

   # On Windows
   go build -o pentora.exe cmd/pentora/main.go
   ```

## 🛠️ Usage

### Quick Scan
Start a comprehensive vulnerability scan against a target URL:
```bash
./pentora scan -u https://example.com
```

### Continuous Asset Radar
Discover subdomains and assets for a given domain:
```bash
./pentora radar -d example.com
```

## ✨ Features
- **AI-Driven Attack Path Analysis**: Predicts compromise paths using a built-in logic engine.
- **Water Breathing UI**: Sleek terminal visuals with Matrix-green banners and progress spinners.
- **Verified Exploits**: Automated proof-of-concept generation for high-fidelity bugs.
- **Fix-it Scripts**: Instant remediation snippets for developers.

## 📄 Reporting
Reports are automatically generated in both `Markdown` and `JSON` formats upon completion of a scan.
