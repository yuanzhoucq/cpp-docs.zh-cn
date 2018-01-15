---
title: "选择透明或不透明背景 （图标的图像编辑器） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- opaque backgrounds
- background colors, images
- colors [C++], image
- Image editor [C++], transparent or opague backgrounds
- background images
- images [C++], transparency
- images [C++], opaque background
- transparent backgrounds
- transparency, background
- transparent backgrounds, images
ms.assetid: 61b743d9-c86b-405d-9a81-0806431b4363
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4e73ac7122b31ab6880d7d27387937113dee70f9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="choosing-a-transparent-or-opaque-background-image-editor-for-icons"></a>选择透明或不透明背景（图标的图像编辑器）
移动或复制选定内容从映像时，任何与匹配的当前的背景色的像素在所选内容时，默认情况下，透明的;它们不清楚目标位置中的像素为单位。  
  
 你可以从透明背景 （默认值） 切换到不透明背景，并切换回。 当您使用选择工具中，**透明背景**和**不透明背景**选项中的选项选择器显示在**图像编辑器**工具栏 （如下所示）。  
  
 ![背景选项 &#45;不透明或透明](../windows/media/vcimageeditoropaqtranspback.gif "vcImageEditorOpaqTranspBack")  
图像编辑器工具栏上的透明和不透明选项  
  
### <a name="to-switch-between-a-transparent-and-opaque-background"></a>若要切换透明的并且不透明背景  
  
1.  在**图像编辑器**工具栏上，单击**选项**选择器，然后单击适当的背景：  
  
    -   **不透明背景 (O)**： 现有映像是否被遮盖由所选内容的所有部分。  
  
    -   **透明背景 (T)**： 透过选定内容中与当前的背景色匹配的部分显示现有映像。  
  
 \- 或 -  
  
-   上**映像**菜单上，选中或清除**绘制不透明**。  
  
 所选内容已经更改图像的哪些部分都是透明的有效时，可以更改背景色。  
  
 有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中*.NET Framework 开发指南。* 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[对于桌面应用程序创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的资源在托管应用中的信息，请参阅[Globalizing 和本地化的.NET Framework 应用程序](/dotnet/standard/globalization-localization/index)。  
  
 惠?  
  
 无  
  
## <a name="see-also"></a>请参阅  
 [快捷键](../windows/accelerator-keys-image-editor-for-icons.md)   
 [处理颜色](../windows/working-with-color-image-editor-for-icons.md)