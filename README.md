# YDW ComfyUI 工作流合集

整理日常使用的 ComfyUI 图像与视频工作流，涵盖 Qwen 图像生成与编辑、角色一致性与人像数据集、Wan 视频生成、SCAIL 动作迁移、JoyCaption 图像描述以及 SeedVR2 放大，方便导入、学习与调整。

本仓库提供工作流 JSON，不包含模型权重、输入素材或生成结果。

## 工作流目录

| 分类 | 文件 | 简介 |
| --- | --- | --- |
| 图像生成 | [Z-image-turbo.json](Z-image-turbo.json) | Z-Image Turbo 文生图，包含 LoRA 加载节点。 |
| 图像生成 | [qwen_image_2512.json](qwen_image_2512.json) | Qwen Image 2512 文生图，包含自定义 LoRA 配置。 |
| 图像编辑 | [my_qwen_image_edit_2511.json](my_qwen_image_edit_2511.json) | Qwen Image Edit 2511 图像编辑。 |
| 图像编辑 | [my-qwen-image-edit-exchangeface.json](my-qwen-image-edit-exchangeface.json) | 基于 Qwen Image Edit 与 LoRA 的人脸替换工作流。 |
| 角色与数据集 | [人物多角度视图一键生成｜Qwen角色一致性分镜出图.json](人物多角度视图一键生成｜Qwen角色一致性分镜出图.json) | 通过循环提示词生成角色多角度视图与分镜素材。 |
| 角色与数据集 | [人像数据集生成.json](人像数据集生成.json) | 组合提示词与参考图，批量生成与保存人像素材。 |
| 图像描述 | [JoyCaption_workflow.json](JoyCaption_workflow.json) | 使用 JoyCaption 描述参考图，并衔接图像生成。 |
| 视频生成 | [Wan2.2-T2V.json](Wan2.2-T2V.json) | Wan 2.2 文生视频，包含高低噪声采样、LoRA 与插帧节点。 |
| 视频生成 | [Wan2.2-I2V.json](Wan2.2-I2V.json) | Wan 2.2 图生视频。 |
| 视频生成 | [Wan2.2-I2V-start-end.json](Wan2.2-I2V-start-end.json) | 通过首帧与尾帧图片控制视频生成。 |
| 视频生成 | [Smooth+Mix+2.0+混合+LightX2V+T2V.json](Smooth+Mix+2.0+混合+LightX2V+T2V.json) | 混合模型与 LightX2V 配置的视频生成工作流。 |
| 视频生成 | [Wan-SkyReels-V3多图参考生成视频.json](Wan-SkyReels-V3多图参考生成视频.json) | 使用多张参考图生成视频，包含插帧与视频导出。 |
| 动作迁移 | [Scail2_多参_无劣化.json](Scail2_多参_无劣化.json) | SCAIL 2 多参考动作迁移，包含视频跟踪、遮罩与上下文窗口。 |
| 动作迁移 | [Scail2动作迁移_for循环.json](Scail2动作迁移_for循环.json) | 使用循环处理的 SCAIL 2 动作迁移工作流。 |
| 放大修复 | [SeedVR2_workflow.json](SeedVR2_workflow.json) | 使用 SeedVR2 放大与修复图像。 |
| 放大修复 | [utility_seedvr2_video_upscale.json](utility_seedvr2_video_upscale.json) | 视频读取、放大处理与导出，包含子图。 |
| 占位文件 | [Scail2-latest.json](Scail2-latest.json)、[wan2.1-SCALL.json](wan2.1-SCALL.json) | 当前节点为空，暂不可直接用于生成。 |

## 如何使用

1. 下载仓库 ZIP，或通过 Git 克隆：

   ```bash
   git clone https://github.com/diweiyin849-del/ydw_comfyui_workflow.git
   ```

2. 启动 ComfyUI，将需要的 JSON 拖入画布，或通过工作流打开菜单导入。
3. 按工作流中的节点信息安装缺失的自定义节点；如使用 ComfyUI Manager，可借助其缺失节点安装功能。
4. 检查模型加载节点，准备对应模型、文本编码器、VAE、CLIP Vision 和 LoRA，并重新选择本机可用的文件。
5. 替换参考图片、视频、文本文件路径及输出前缀，调整提示词、尺寸、帧数与采样参数后运行。

## 模型与节点说明

- 图像工作流涉及 Qwen Image、Qwen Image Edit、Z-Image Turbo 及其相关模型。
- 视频工作流涉及 Wan 2.2、SkyReels V3、SCAIL 2，以及部分 LightX2V 加速 LoRA。
- 部分工作流使用 Easy Use、KJNodes、rgthree、VideoHelperSuite、LayerStyle、Comfyroll、RIFE、SAM3、JoyCaption、SeedVR2 等扩展；具体依赖以导入后的节点信息为准。
- 模型加载节点保留了原来的文件名，部分是个人 LoRA。缺少对应文件时，请提供兼容模型并调整配置；不使用的可选 LoRA 节点可按连接关系旁路。
- 不同工作流对显存的需求不同，请结合本机资源调整分辨率、批量大小、视频帧数与模型精度。

## 仓库说明

- 根目录 JSON 是原始工作流，保留现有名称与配置。
- `.index.json` 是本地工作流收藏索引，不参与生成，本仓库不提交该文件。
- 本次整理检查了 JSON 是否可解析与节点内容，未在 ComfyUI 中执行生成验证。
- 模型及自定义节点的使用条件以各自项目为准。
