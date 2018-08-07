---
title: 保存和加载不同的调色板 （图标的图像编辑器） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.image.color
dev_langs:
- C++
helpviewer_keywords:
- color palettes [C++]
- palettes
- palettes, Image editor
- colors [C++], Image editor
- Image editor [C++], palettes
ms.assetid: 694b6346-e606-4f19-aa01-9b4ceb47f423
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 14cad19c53e8cd741bf16bab49420169e93f6af6
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2018
ms.locfileid: "39606967"
---
# <a name="saving-and-loading-different-color-palettes-image-editor-for-icons"></a>保存和加载不同的调色板（图标的图像编辑器）
可以保存和加载包含的颜色调色板[自定义颜色](../windows/customizing-or-changing-colors-image-editor-for-icons.md)。 （默认情况下，启动 Visual Studio 时，会自动加载最近使用的调色板。）  
  
> [!TIP]
>  由于图像编辑器无法还原默认调色板，所以你应保存默认调色板（名称如 standard.pal 或 default.pal），这样便可轻松还原默认设置。  
  
### <a name="to-save-a-custom-colors-palette"></a>保存自定义调色板  
  
1.  从**图像**菜单中，选择**保存调色板**。  
  
2.  导航到要用于保存调色板的目录并键入调色板的名称。  
  
3.  单击“保存” 。  
  
### <a name="to-load-a-custom-colors-palette"></a>加载自定义调色板  
  
1.  从**图像**菜单中，选择**加载调色板**。  
  
2.  在中[加载调色板对话框](../windows/load-palette-colors-dialog-box-image-editor-for-icons.md)，导航到正确的目录，然后选择你想要加载的调色板。 以 .pal 文件扩展名保存调色板。  
  
## <a name="requirements"></a>要求  
  
 无  
  
## <a name="see-also"></a>请参阅  
 [加速键](../windows/accelerator-keys-image-editor-for-icons.md)   
 [处理颜色](../windows/working-with-color-image-editor-for-icons.md)