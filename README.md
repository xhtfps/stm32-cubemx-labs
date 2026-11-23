# STM32 CubeMX 与标准库工程集

STM32 学习过程中的工程集：CubeMX 生成的 HAL 工程（LED / KEY / TIM / USART / ADC / FreeRTOS 等），以及一套标准外设库（HAL_project）工程模板。

## 目录一览

- `HAL_project`/
- `cube MX project`/

## 说明

- 只收录**可版本化的源码、文档与小型资源**；编译中间产物、IDE 缓存、安装包、视频、镜像、数据集与模型权重按规则排除。
- 被排除文件的摘要见 [`EXCLUDED_FILES.md`](EXCLUDED_FILES.md)（条目规模、总体积与排除原因分布）；逐文件明细临时生成，不入库。
- 第三方资料版权归原作者，仅作学习参考。

_由本地目录整理归档，10219 个文件。_

## 大文件去哪了

本仓已做过体积治理：大文件从当前分支移出，但历史提交完整保留，随时可取回。

- **其它产物**：各 lab 重复的 CMSIS 副本 13 MB 与 10 MB 逐文件清单 CSV，提交 `91daec0d`。
- **完整台账**：[`notes/offload.json`](https://github.com/xhtfps/notes/blob/main/offload.json)（repo / path / size / base_commit），恢复命令与口径见索引仓 [`SLIM-PLAN.md`](https://github.com/xhtfps/xhtfps/blob/main/SLIM-PLAN.md)。

clone 后发现某个文件不在，按台账里的 `base_commit` 打开 `https://github.com/xhtfps/<repo>/blob/<base_commit>/<path>` 取回即可，不要重复提交进仓。
