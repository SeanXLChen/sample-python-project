# Poetry Demo

A demo project using Poetry for dependency management.

## Setup

1. Create and activate the conda environment (if not already created):
```bash
conda create -n poetry-demo python=3.11 
conda activate poetry-demo
```

2. (Recommended, run once) Configure Poetry to use the current conda environment, not a separate venv:
```bash
poetry config virtualenvs.create false
```
> This command can (and should) be run inside your conda environment. It ensures Poetry will use your active conda environment instead of creating a new virtualenv. Otherwise, Poetry will default to creating a separate virtual environment in `~/.cache/pypoetry/virtualenvs`, which may conflict with your conda environment.

3. (For new projects) Initialize Poetry in your project folder (if you don't have a `pyproject.toml` yet):
```bash
poetry init
```
Follow the prompts to set up your project dependencies.

4. Install project dependencies:
```bash
poetry install
```

---

**Tip:** Always activate your conda environment before running any Poetry commands for this project:
```bash
conda activate poetry-demo
```

---

完成上述步骤后，你就可以直接运行你的 Python 代码了，所有依赖都已准备好，无需额外操作！

## 依赖管理（添加/移除依赖）

在已激活 conda 环境的前提下，可以用以下命令管理项目依赖：

### 添加依赖
```bash
poetry add <包名>
```
例如，添加 requests：
```bash
poetry add requests
```

### 移除依赖
```bash
poetry remove <包名>
```
例如，移除 requests：
```bash
poetry remove requests
```

这些命令会自动更新 `pyproject.toml` 并在当前环境中安装/卸载对应包。

> **注意：** 每次操作前请确保已激活 conda 环境（`conda activate poetry-demo`），以保证依赖被正确安装或移除。

每次添加或移除依赖后，建议重新运行 `poetry install`，以确保 lock 文件和环境同步。

## 仅用 Poetry 管理依赖（非打包项目）

如果你只想用 Poetry 管理依赖，不打算把项目做成 Python 包（即没有自己的包目录），建议在 `pyproject.toml` 末尾加上：

```toml
[tool.poetry]
package-mode = false
```

这样 Poetry 安装依赖时不会强制要求本地包结构，也不会报错。

> **说明：** 该设置适用于只做依赖管理、不需要发布为 PyPI 包的项目。 