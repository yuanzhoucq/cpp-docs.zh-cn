---
title: “自定义生成步骤”属性页：常规 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- VC.Project.VCCustomBuildStep.AdditionalInputs
- VC.Project.VCCustomBuildStep.CustomBuildAfterTargets
- VC.Project.VCCustomBuildStep.CustomBuildBeforeTargets
- VC.Project.VCCustomBuildStep.Outputs
- VC.Project.VCCustomBuildStep.Message
- VC.Project.VCCustomBuildStep.Command
dev_langs:
- C++
helpviewer_keywords:
- project properties, custom build step
- custom build step (general)
ms.assetid: bd319741-0491-46c4-a428-7c61b4b46a02
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5d88bd738711058794a525217ba2640e8d52356d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33325924"
---
# <a name="custom-build-step-property-page-general"></a>“自定义生成步骤”属性页：常规
对于你的项目中项目配置和目标平台的每种组合，你可以在项目生成时指定要执行的自定义步骤。  

有关此页的 Linux 版本，请参阅[自定义生成步骤属性 (Linux C++)](../linux/prop-pages/custom-build-step-linux.md)。
  
## <a name="uielement-list"></a>UIElement 列表  
 **命令行**  
 将由自定义生成步骤执行的命令。  
  
 **说明**  
 自定义生成步骤运行时显示的消息。  
  
 **输出**  
 自定义生成步骤生成的输出文件。 需要该设置，以使增量生成正确执行。  
  
 **附加依赖项**  
 用于自定义生成步骤的任何其他输入文件的以分号分隔的列表。  
  
 **在以下操作之后执行和在以下操作之前执行**  
 这些选项定义相对于列出的目标，何时在生成过程中运行自定义生成步骤。 最常列出的目标是 BuildGenerateSources、BuildCompile 和 BuildLink，因为它们代表生成过程中的主要步骤。 其他经常列出的目标是 Midl、CLCompile 和链接。  
  
 将输出视为内容  
 该选项只对于通用 Windows 平台应用或 Windows Phone 应用有意义，这些应用将所有内容文件包含在 .appx 包中。  
  
### <a name="to-specify-a-custom-build-step"></a>指定自定义生成步骤  
  
1.  在菜单栏上，依次选择“项目”、“属性”。 有关详细信息，请参阅[使用项目属性](../ide/working-with-project-properties.md)。  
  
2.  在“属性页”对话框中，导航到“配置属性”->“自定义生成步骤”->“常规”页面。  
  
3.  修改设置。  
  
## <a name="see-also"></a>请参阅  
 [属性页](../ide/property-pages-visual-cpp.md)