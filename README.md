# Poetry Demo

一个演示如何结合 Conda 和 Poetry 进行依赖管理的项目。

## 环境搭建

1. 创建并激活 conda 环境（如未创建）：
```bash
conda create -n poetry-demo python=3.11
conda activate poetry-demo
```

2. （推荐，仅需执行一次）配置 Poetry 使其使用当前 conda 环境，而不是单独创建 venv：
```bash
poetry config virtualenvs.create false
```
> 该命令建议在 conda 环境内执行。这样 Poetry 会直接使用你激活的 conda 环境，而不会在 `~/.cache/pypoetry/virtualenvs` 下新建虚拟环境，避免冲突。

3. （新项目需）初始化 Poetry（如果还没有 `pyproject.toml`）：
```bash
poetry init
```
根据提示填写依赖。

4. 安装项目依赖：
```bash
poetry install
```

---

**提示：** 每次操作 Poetry 相关命令前，请先激活 conda 环境：
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