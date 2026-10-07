# miniDB

一个使用 C 语言编写的简单数据库教程项目。

本项目参考了 [cstack/db_tutorial](https://github.com/cstack/db_tutorial)，感谢原作者提供的优秀教程和清晰的实现思路。

## 开发环境

项目使用 WSL 2、Ubuntu、GCC 和 GNU Make 编译运行。

### 安装 WSL 和 Ubuntu

在 Windows PowerShell 中执行：

```powershell
wsl --install -d Ubuntu
```

安装完成后，启动 Ubuntu：

```powershell
wsl -d Ubuntu
```

### 安装编译工具

进入 Ubuntu 后执行：

```bash
sudo apt update
sudo apt install ruby-full ruby-dev ruby-bundler build-essential
```

如果要运行测试，在项目目录中执行：

```bash
bundle config set --local path vendor/bundle
bundle install
```

## 编译和运行

克隆仓库后，在 Ubuntu/WSL 终端中进入项目目录：

```bash
cd miniDB
```

编译项目：

```bash
make db
```

运行项目：

```bash
make run
```

也可以直接运行编译生成的程序：

```bash
./db
```

程序启动后会显示 `db >`，输入以下命令退出：

```text
.exit
```

## Makefile 命令

```bash
make db       # 编译 db.c
make run      # 编译并运行程序
make clean    # 清理编译文件和数据库文件
make format   # 使用 clang-format 格式化 C 文件
make test     # 运行测试
```

如果使用 VS Code，可以安装 WSL 扩展，并通过命令面板执行 `WSL: Reopen Folder in WSL`，然后在 VS Code 的 Ubuntu 终端中运行上述命令。

## 发布 Release

本项目使用语义化版本号，并通过预发布后缀区分非生产版本：

- `v0.1.0-alpha.1`：早期实验版本，功能可能变化
- `v0.1.0-beta.1`：功能基本稳定，但仍不建议用于生产环境
- `v0.1.0`：稳定版本

发布流程由 GitHub Actions 自动完成。推送符合 `v*` 格式的标签后，Actions 会先安装依赖并运行 `make test`；测试通过后读取 Release 模板、生成 changelog、组合完整的 Release 正文，最后创建 GitHub Release 并上传源代码压缩包。带有 `-alpha` 或 `-beta` 后缀的版本会自动标记为预发布版本。

例如，发布一个非生产版本：

```bash
git tag -a v0.1.0-alpha.1 -m "release: v0.1.0-alpha.1"
git push origin v0.1.0-alpha.1
```

Release 描述模板见 [`RELEASE_TEMPLATE.md`](.github/RELEASE_TEMPLATE.md)。工作流会自动替换版本号、版本状态、提交范围和 changelog，不需要手动编辑 Release 正文。
