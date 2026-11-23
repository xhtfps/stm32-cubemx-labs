# STM32 CubeMX 与标准库工程集

STM32 学习过程中的工程集合：CubeMX 生成的 HAL 工程（LED / KEY / TIM / USART / ADC / FreeRTOS 等），以及一套标准外设库工程模板。用来对照“同一外设的 HAL 写法与 StdPeriph 写法差在哪”。

## 1. 工程清单与对应外设

| 工程目录 | 外设 / 主题 | 说明 |
| --- | --- | --- |
| `HAL_project/` | GPIO、USART、TIM | 标准库模板，学寄存器与外设库差异的基准 |
| `cube MX project/` 下各 lab | LED / KEY / TIM / USART / ADC / I2C / SPI / FreeRTOS | CubeMX 生成，每个 lab 一个独立 `.ioc`，可直接重新生成 |

每个 lab 自带完整 `Drivers/`（HAL + CMSIS），**clone 即可用 Keil / CubeIDE 打开编译**，不需要额外拉依赖。

## 2. 怎么用

1. 用 STM32CubeIDE 或 Keil（需装对应器件包）打开 `cube MX project/<lab>` 下的工程文件。
2. 想改配置：用 CubeMX 打开同目录 `.ioc`，重新生成代码后再编译，避免手改 `Core/` 里的生成段落。
3. 对照学习：先看 `HAL_project` 的 StdPeriph 写法，再看同名 lab 的 HAL 写法，差异最集中的是时钟使能与中断配置两处。

## 3. 体积治理约定

- 只收录**可版本化的源码、文档与小型资源**；编译中间产物、IDE 缓存、安装包、视频、镜像、数据集与模型权重按规则排除。
- 各 lab 重复的 CMSIS 副本（13 MB）已移除，提交 `91daec0d`；只依赖该副本的工程需从 ST 官网补回。
- 10 MB 的逐文件清单 `EXCLUDED_MANIFEST.csv` 改为 [`EXCLUDED_FILES.md`](EXCLUDED_FILES.md) 摘要；逐文件明细临时生成，不入库。
- 第三方资料版权归原作者，仅作学习参考。

## 4. 状态

在用。新 lab 按“一 lab 一目录、带 `.ioc`、不放大文件”的约定增量添加。

## 大文件去哪了

本仓已做过体积治理：大文件从当前分支移出，但历史提交完整保留，随时可取回。

- **其它产物**：各 lab 重复的 CMSIS 副本 13 MB 与 10 MB 逐文件清单 CSV，提交 `91daec0d`。
- **完整台账**：[`notes/offload.json`](https://github.com/xhtfps/notes/blob/main/offload.json)（repo / path / size / base_commit）；恢复口径见 [`SLIM-PLAN.md`](https://github.com/xhtfps/xhtfps/blob/main/SLIM-PLAN.md)。

clone 后发现某个文件不在，按台账里的 `base_commit` 打开 `https://github.com/xhtfps/<repo>/blob/<base_commit>/<path>` 取回即可，不要重复提交进仓。
