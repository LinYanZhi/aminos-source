# Aminos Source

aminos 的软件源定义仓库，供 [aminos](https://github.com/LinYanZhi/aminos) 包管理器使用。

## 目录结构

```
aminos-source/
├── apps/             ← 第三方软件源定义
│   ├── index.json          # 源索引
│   ├── chrome.json         # Google Chrome
│   ├── vscode.json         # Visual Studio Code
│   └── ...
└── tools/            ← 自研工具源定义
    ├── index.json          # 工具索引
    ├── ls.json             # ls 工具
    ├── uv.json             # uv 工具
    └── as/                 # 工具二进制 ZIP（被 JSON 引用）
        └── as.zip
```

## 使用方式

```cmd
# 更新第三方软件源
as env source update

# 查看可用软件
as list

# 安装第三方软件
as install chrome

# 查看/安装自研工具
as tool list
as tool install ls
```

## 如何添加软件

### 第三方软件

1. 在 `apps/` 目录下创建 `<name>.json`
2. 更新 `apps/index.json` 添加对应的 SHA256
3. 提交 PR

### 自研工具

1. 在 `tools/` 目录下创建 `<name>.json`
2. 将二进制 ZIP 放到 `tools/<name>/<name>.zip`
3. 更新 `tools/index.json` 添加对应的 SHA256
4. 提交 PR

## JSON 格式

### 第三方软件

```json
{
  "name": "7zip",
  "display_name": "7-Zip",
  "description": "免费开源的文件压缩/解压工具",
  "category": "工具",
  "default_version": "26.01",
  "versions": {
    "26.01": {
      "urls": ["https://7-zip.org/a/7z2601-x64.exe"],
      "installer_type": "nsis",
      "install_args": ["/S"],
      "detection": {
        "display_name": "7-Zip"
      }
    }
  }
}
```

### 自研工具

```json
{
  "name": "ls",
  "description": "增强版目录列表工具",
  "default_version": "0.1.0",
  "versions": {
    "0.1.0": {
      "urls": ["https://raw.githubusercontent.com/LinYanZhi/aminos-source/main/tools/ls/ls.zip"],
      "entry_point": "ls.exe"
    }
  }
}
```

## 许可证

MIT
