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
sudo apt install build-essential
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
