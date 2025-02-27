### 数据集下载

[数据集下载](../../benchmarks/tacotron2/README.md#数据集下载地址)

### 天数智芯 BI-V100 GPU配置与运行信息参考
#### 环境配置
- ##### 硬件环境
    - 机器、加速卡型号: Iluvatar BI-V100 32GB

- ##### 软件环境
   - OS版本：Ubuntu 20.04
   - OS kernel版本:  5.4.0-148-generic x86_64    
   - 加速卡驱动版本：3.1.0
   - Docker 版本：20.10.21
   - 训练框架版本：torch-1.13.1+corex.3.1.0
   - 依赖软件版本：无



### 运行情况
* 通用指标

| 指标名称       | 指标值                  | 特殊说明                                    |
| -------------- | ----------------------- | ------------------------------------------- |
| 任务类别       | SpeechSynthesis         |                                             |
| 模型           | tacotron2               |                                             |
| 数据集         | LJSpeech                |                                             |
| 数据精度       | precision,见“性能指标”  | 可选fp32/amp/fp16/tf32                      |
| 超参修改       | fix_hp,见“性能指标”     | 跑满硬件设备评测吞吐量所需特殊超参          |
| 硬件设备简称   | nvidia A100             |                                             |
| 硬件存储使用   | mem,见“性能指标”        | 通常称为“显存”,单位为GiB                    |
| 端到端时间     | e2e_time,见“性能指标”   | 总时间+Perf初始化等时间                     |
| 总吞吐量       | p_whole,见“性能指标”    | 实际训练样本数除以总时间(performance_whole) |
| 训练吞吐量     | p_train,见“性能指标”    | 不包含每个epoch末尾的评估部分耗时           |
| **计算吞吐量** | **p_core,见“性能指标”** | 不包含数据IO部分的耗时(p3>p2>p1)            |
| 训练结果       | val_loss,见“性能指标”   | 验证loss                                    |
| 额外修改项     | 无                      |                                             |

* 性能指标

| 配置               | precision|    fix_hp       | e2e_time | p_whole | p_train | p_core | val_loss | mem       |
|--------------------| ---------| ----------------| ---------| ------- | ------- | ------ | -------- | --------- |
| BI100单机8卡(1x8)  | tf32     | bs=64, lr=0.001 | 41220    | 33082    | 33289   | 33511  | 0.4833  | 18.4/32.0  |

