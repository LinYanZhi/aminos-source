# Aminos Source

aminos 的软件源定义仓库，供 [aminos](https://github.com/LinYanZhi/aminos) 命令行工具使用。

## 目录结构

```
source/
├── index.json          # 源索引（供 as source update 拉取）
├── 7zip.json           # 7-Zip
├── chrome.json         # Google Chrome
├── ...                 # 更多软件
```

## 如何添加软件

1. Fork 本仓库
2. 参考现有 JSON 文件创建新的软件定义
3. 更新 `index.json` 添加新文件
4. 提交 PR

## JSON 格式

```json
{
  "name": "7zip",
  "display_name": "7-Zip",
  "aliases": ["7-zip", "7z"],
  "description": "免费开源的文件压缩/解压工具",
  "category": "工具",
  "homepage": "https://7-zip.org/",
  "default_version": "26.01",
  "versions": {
    "26.01": {
      "urls": ["https://7-zip.org/a/7z2601-x64.exe"],
      "arch": "x64",
      "installer_type": "nsis",
      "install_args": ["/S"],
      "detection": {
        "display_name": "7-Zip",
        "publisher": "Igor Pavlov"
      }
    }
  }
}
```

## 使用方式

aminos 工具会自动从本仓库拉取软件定义：

```cmd
# 首次运行自动拉取
as list

# 手动更新源
as source update
```

## 许可证

MIT
