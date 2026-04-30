# 中文 LaTeX 极简模板 (基于 Devbox + Tectonic)

这是一个基于 [Devbox](https://www.jetify.com/devbox) 和 [Tectonic](https://tectonic-typesetting.github.io/) 构建的现代化中文 LaTeX 项目模板。通过 Devbox 提供可复现的隔离环境，免去了手动安装庞大 TeX Live 的烦恼，实现真正的开箱即用。

## ✨ 核心特性

- **环境完全隔离**: 编译引擎、格式化工具和检查工具均由 Devbox 管理，零全局污染。
- **按需下载宏包**: Tectonic 在编译时会自动在云端获取需要的 LaTeX 宏包，摆脱传统几个 G 大小的本地安装包。
- **极简单文件结构**: 采用最轻量的单 `main.tex` 结构，适合小论文、作业和简历撰写。
- **完美融合 VS Code**: 已配妥包含编译、格式化 (`tex-fmt`) 及实时语法检查 (`chktex`) 等功能的完善配置。

## 🚀 快速上手

### 1. 准备工作

请确保您的系统已经安装了 [Devbox](https://www.jetify.com/devbox/docs/installing_devbox/)。为了达到最佳无缝体验，强烈推荐安装并配置好 [direnv](https://direnv.net/)。

### 2. 环境初始化

当您进入本目录时，如果您使用了 `direnv`，首先需要通过 devbox 生成 `.envrc` 文件（如果尚未生成或 devbox.json 发生了改变）：

```bash
devbox generate direnv
```

然后允许 `direnv` 加载环境：

```bash
direnv allow
```

如果您没有使用 `direnv`，可以通过以下命令手动激活开发环境：

```bash
devbox shell
```

### 3. 快捷命令

项目中已为您内置了若干便捷脚本，直接在终端即可使用：

- **编译生成 PDF**
  ```bash
  devbox run build
  ```
  *(基于 Tectonic 引擎，生成文件为 `main.pdf`)*

- **格式化代码**
  ```bash
  devbox run fmt
  ```

- **静态代码检查**
  ```bash
  devbox run lint
  ```

## 💻 VS Code 终极体验

强烈建议在 VS Code 中安装以下插件：
1. **LaTeX Workshop** (`James-Yu.latex-workshop`)：LaTeX 核心插件。
2. **direnv** (`mkhl.direnv`)：自动为 VS Code 加载 Devbox 路径环境。

本项目的 `.vscode/settings.json` 已帮您打通了一切：
- **无感编译**：默认使用 Tectonic 工具链，并支持 PDF 正反向跳转 (SyncTeX)。
- **实时规范**：保存即自动采用 `tex-fmt` 进行格式化。
- **实时查错**：自动通过 `chktex` 在代码中提示警告和建议。

## 📂 目录结构说明

```text
.
├── .vscode/               # 包含 LaTeX Workshop 运行的所有优化配置
├── main.tex               # 您的核心 LaTeX 源码文件
├── main.pdf               # 编译生成的 PDF 文件
├── devbox.json            # 包含所有必需依赖以及快捷 Scripts 定义
├── .envrc                 # 由 devbox generate direnv 自动生成的环境变量挂载配置文件
├── .editorconfig          # 统一样板代码缩进和编码格式
└── .gitignore             # Git 忽略配置（忽略中间过程产物）
```
