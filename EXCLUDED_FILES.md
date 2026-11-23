# 被排除文件摘要

本仓由本地目录一次性归档，入库范围只含可版本化的源码、文档与小体积资源。逐文件排除清单（路径 / 体积 / 原因）体量约 **10 MB**，不适合放在 Git 历史里，故不入库，改为本文摘要 + 现场生成。

## 排除范围

| 类别 | 典型内容 | 判断口径 |
| --- | --- | --- |
| 编译中间产物 | `*.o`、`*.d`、`*.crf`、`*.axf`、`*.hex`、`*.bin`、`Objects/`、`Listings/` | 可由源码重建，一律不入库 |
| IDE 与工具缓存 | `.vscode/`、`.idea/`、`*.uvguix.*`、`.mxproject` 备份、`DebugConfig/` | 本机状态，换机器即失效 |
| 安装包与工具 | `*.exe`、`*.msi`、`*.zip` 安装包、Keil/CubeMX 离线包 | 体积大且可再下载 |
| 视频、镜像、数据集 | `*.mp4`、`*.iso`、`*.img`、数据集压缩包、模型权重 | 体积与 Git 不兼容 |
| 厂家资料原件 | 芯片手册 PDF、开发板原理图 PDF、官方例程压缩包 | 登记在 `notes` 仓手册索引表，仓内只留链接与版本号 |

## 如何重新生成逐文件明细

在有网、已登录 `gh` 的机器上，用索引仓的审计脚本现场生成（输出到本地临时目录，不要提交）：

```powershell
# 在 index 仓根目录
pwsh ./tools/repo-audit.ps1 -Owner xhtfps -Repo stm32-cubemx-labs -OutFile $env:TEMP\cubemx-excluded.csv
```

脚本按 `REPO-STANDARD.md` 的排除规则枚举工作区文件，输出 `path,size_bytes,reason` 三列 CSV。

## 约定

- 新增排除类别时，先改 `index` 仓的 `REPO-STANDARD.md`，再改本文的类别表，两处保持一致。
- 若某个“被排除”文件其实要长期保存，应移到专门的资料仓（如 `stm32f4-reference-materials`）或 `notes` 手册索引，而不是塞回本仓。
