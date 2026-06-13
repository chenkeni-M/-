# -[README.md](https://github.com/user-attachments/files/28909753/README.md)
# 文档转换工具

一个脚本搞定 PDF、Word、Excel 三种格式的转换，自动识别格式，不覆盖已有文件。

## 快速开始

```bash
# 终端里用（最常用）
./convert/启动转换.command
# → 输入或拖入文件路径 → 自动识别转换

# 直接指定文件
./convert/启动转换.command ~/Documents/合同.pdf
./convert/启动转换.command ~/Documents/意见书.docx
./convert/启动转换.command ~/Documents/报表.xlsx

# Finder 双击 → 弹窗选文件
```

## 支持的格式

| 输入 | 输出 | 依赖 | 说明 |
|------|------|------|------|
| `.pdf` | `.md` | MinerU 3.3.1 | 支持扫描件 OCR，保留标题/表格/公式 |
| `.docx` `.doc` | `.md` | mammoth + textutil | `.doc` 自动转换后处理 |
| `.xls` `.xlsx` `.xlsm` `.et` | `.json` | pandas + openpyxl + xlrd | 每个 sheet 导出为独立 JSON |

## 输出位置

```
convert/output/
├── md/          ← PDF、Word 转换结果
└── json/        ← Excel 转换结果
```

输出**保持原目录结构**。如果输出文件已存在，自动加上时间戳后缀，**不会覆盖**：

```
合同.md                          ← 第一次
合同.md_20250613-161823          ← 第二次自动加时间戳
```

## 目录结构

```
convert/
├── 启动转换.command    ← 唯一入口，所有功能在这一文件里
├── output/             ← 输出目录
└── README.md
```

## 环境

- macOS + .venv（Python 3.12）
- MinerU 模型已通过 ModelScope 下载（国内可用，无需翻墙）
- 首次运行 PDF 转换需约 12 秒初始化模型，之后更快
