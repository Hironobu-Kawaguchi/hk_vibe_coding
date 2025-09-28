# AGENTS.md

## Policy

### Development Steps
- Prototyping
- MVP (Minimum Viable Product)
- PMF (Product-Market Fit)

### Development Principles

- **Spec-Driven Development (SDD):** Each specification is tracked as a single issue.
- **Test-Driven Development (TDD):** Red-Green-Refactor cycle for all code changes.
- **Good Practices:**
  - Make only necessary changes (no out-of-scope modifications)
  - Minimize dependencies
  - Maintain high code quality
  - Prefer clarity and simplicity over cleverness
  - Keep commit history organized and meaningful
  - Write clear, concise, and informative docstrings
  - Ensure code is easy to review and maintain
  - Use automated tests, code formatting tools, and linters
  - Always use an appropriate .gitignore to exclude unnecessary files and directories from version control.

### Reproducibility & Traceability

- **Virtual Environment Isolation:** Use virtual environments to isolate dependencies.
- **Git Change Management:** Simple branching, minimal conventional commits.
- **Logging:** Maintain good logging practices.

---

## Tech Stack

Current Versions and Environment Information:

### Computer Resource
```text
Model Name: MacBook Pro
Model Identifier: Mac16,6
Model Number: Z1FG00357J/A
Chip: Apple M4 Max
Total Number of Cores: 16 (12 performance and 4 efficiency)
Memory: 128 GB
System Firmware Version: 11881.140.96
OS Loader Version: 11881.140.96
Serial Number (system): HXRHXM9X9P
Hardware UUID: E8FB9919-0815-53D2-B11C-1F9B0C796C64
Provisioning UDID: 00006041-001A30980C20801C
Activation Lock Status: Enabled
```
*To check hardware details:*
```zsh
system_profiler SPHardwareDataType
```

### macOS
```text
ProductName:    macOS
ProductVersion: 15.6.1
BuildVersion:   24G90
```
*To check macOS version:*
```zsh
sw_vers
```

### Python (uv)
```text
uv 0.8.22 (Homebrew 2025-09-23)
```
*To check uv version:*
```zsh
uv -V
```

### Node.js
```text
v24.9.0
```
*To check Node.js version:*
```zsh
node -v
```

### npm
```text
11.6.0
```
*To check npm version:*
```zsh
npm -v
```

### Git
```text
git version 2.39.5 (Apple Git-154)
```
*To check Git version:*
```zsh
git --version
```

### Homebrew
``` text
Homebrew 4.6.14
```

*To check Homebrew version:*
``` zsh
brew -v
```

### uv tools
```text
mlx-lm v0.28.1
- mlx_lm.awq
- mlx_lm.benchmark
- mlx_lm.cache_prompt
- mlx_lm.chat
- mlx_lm.convert
- mlx_lm.dwq
- mlx_lm.dynamic_quant
- mlx_lm.evaluate
- mlx_lm.fuse
- mlx_lm.generate
- mlx_lm.gptq
- mlx_lm.lora
- mlx_lm.manage
- mlx_lm.perplexity
- mlx_lm.server
- mlx_lm.upload
plamo-translate v1.0.4
- plamo-translate
specify-cli v0.0.17
- specify
```
*To list installed uv tools:*
```zsh
uv tool list
```

### Docker
```text
Docker version 28.3.2, build 578ccf6
```
*To check Docker version:*
```zsh
docker --version
```

### VS Code
```text
1.104.2
e3a5acfb517a443235981655413d566533107e92
arm64
```
*To check VS Code version:*
```zsh
code --version
```
