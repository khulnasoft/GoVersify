# Goversify

<p align="center">
  <a href="https://github.com/khulnasoft/goversify/actions/workflows/test.yml">
    <img src="https://github.com/khulnasoft/goversify/workflows/Test/badge.svg?branch=main" alt="Build Status">
  </a>
  <a href="https://goreportcard.com/report/github.com/khulnasoft/goversify">
    <img src="https://goreportcard.com/badge/github.com/khulnasoft/goversify" alt="Go Report Card">
  </a>
  <a href="https://pkg.go.dev/github.com/khulnasoft/goversify">
    <img src="https://pkg.go.dev/badge/github.com/khulnasoft/goversify.svg" alt="Go Reference">
  </a>
  <a href="https://opensource.org/licenses/MIT">
    <img src="https://img.shields.io/github/license/khulnasoft/goversify" alt="License">
  </a>
  <a href="https://github.com/khulnasoft/goversify/stargazers">
    <img src="https://img.shields.io/github/stars/khulnasoft/goversify?style=social" alt="GitHub Stars">
  </a>
</p>

Goversify is a powerful Go library for parsing, comparing, and validating version constraints. It supports **Semantic Versioning (SemVer)** and **extended versioning schemes**, making it ideal for version management and dependency resolution.

## Features
- ✅ **Strict SemVer Parsing**: Ensures compliance with [Semantic Versioning](https://semver.org/).
- ✅ **Version Sorting & Comparison**: Handles pre-release versions correctly.
- ✅ **Flexible Constraints**: Supports logical operators (`>`, `<`, `>=`, `<=`, `!=`, `~`, `^`), wildcards (`x`, `X`, `*`), and complex constraints (`AND` & `OR`).
- ✅ **Extended Versioning**: Supports versions beyond MAJOR.MINOR.PATCH.
- ✅ **Go-Native & Lightweight**: No external dependencies.

---

## 📖 Table of Contents
- [Installation](#installation)
- [Usage](#usage)
  - [SemVer](#semver)
  - [Version](#version)
  - [Constraints](#constraints)
- [Examples](#examples)
- [License](#license)

---

## 🚀 Installation
```sh
go get github.com/khulnasoft/goversify
```

---

## 🛠️ Usage
### SemVer
```go
v1, _ := semver.Parse("1.2.0")
v2, _ := semver.Parse("1.2.1")

if v1.LessThan(v2) {
    fmt.Printf("%s is less than %s", v1, v2)
}
```
### Sorting Versions
```go
versionsRaw := []string{"1.1.0", "0.7.1", "1.4.0", "1.4.0-alpha"}
versions := make([]semver.Version, len(versionsRaw))
for i, raw := range versionsRaw {
    v, _ := semver.Parse(raw)
    versions[i] = v
}
sort.Sort(semver.Collection(versions))
```

### Constraint Validation
```go
v, _ := semver.Parse("2.1.0")
c, _ := semver.NewConstraints(">= 1.0, < 1.4 || > 2.0")

if c.Check(v) {
    fmt.Printf("%s satisfies constraints '%s'", v, c)
}
```

---

## 🎯 Supported Constraint Operators
- `=` : Exact match
- `!=` : Not equal
- `>` / `<` : Greater / Less than
- `>=` / `<=` : Greater / Less than or equal
- `^` : Compatible updates (`^1.2.3` → `>=1.2.3, <2.0.0`)
- `~` : Patch-level updates (`~1.2.3` → `>=1.2.3, <1.3.0`)
- `*`, `x`, `X` : Wildcard support (`2.0.x` → `>=2.0.0, <2.1.0`)

---

## 📌 Examples
Check out the [examples](./examples/) directory for more in-depth usage.

---

## 📜 License
Goversify is licensed under the [MIT License](./LICENSE).

---

### 🌟 Contribute
We welcome contributions! Feel free to open issues and submit PRs. 😊

