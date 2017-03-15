---
title: "Specifying the Location and Size of a Dialog Box | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "dialog boxes, size"
  - "dialog boxes, positioning"
ms.assetid: 2b7c495e-6595-4cfb-9664-80b2826d0851
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Specifying the Location and Size of a Dialog Box
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

对话框的位置和大小以及其中的控件的位置和大小以对话框单元度量。  当选择个别控件和对话框时，它们的值出现在 Visual Studio 状态栏的右下方。  
  
 在[“属性”窗口](../Topic/Properties%20Window.md)中，可以设置三个属性来指定对话框在屏幕上出现的位置。  Center 属性是布尔型；如果将其设置为 True，则对话框将总是出现在屏幕的中央。  如果设置为 False，则需要设置 XPos 和 YPos 属性以显式定义对话框在屏幕上出现的位置。  位置属性是从查看区域左上角（定义为 {X\=0, Y\=0}）偏移的值。  位置还基于 **Absolute Align** 属性：如果其为 True，则坐标相对于屏幕；如果为 False，则坐标相对于对话框所有者的窗口。  
  
 有关将资源添加到托管项目的信息，请参见“.NET Framework 开发员指南”中的[应用程序中的资源](../Topic/Resources%20in%20Desktop%20Apps.md)。有关手动将资源文件添加到托管项目、访问资源、显示静态资源和将资源字符串分配给属性的信息，请参见[演练：本地化 Windows 窗体](http://msdn.microsoft.com/zh-cn/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
## 要求  
 Win32  
  
## 请参阅  
 [Controls in Dialog Boxes](../mfc/controls-in-dialog-boxes.md)   
 [控件](../mfc/controls-mfc.md)