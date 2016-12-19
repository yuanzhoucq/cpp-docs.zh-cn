---
title: "Item cannot be added to the Toolbox. | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.message.VB_E_NOTSUPPORTEDDATA"
  - "vs.message.0x800A0065"
ms.assetid: 69fa5e73-bbc6-462c-95ca-bf2ee32d43ff
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Item cannot be added to the Toolbox.
尝试添加工具箱无法显示其对应快捷方式图标的项时，通常会发生此错误。  
  
 工具箱可以显示的项包括：  
  
-   本地计算机上安装的控件和 .NET Framework 组件。  
  
 **注意** 对于 [!INCLUDE[vstecasp](../misc/includes/vstecasp_md.md)] Web 窗体的控件和组件，工具箱中显示的对应 [AspNetHostingPermission.Level 属性](https://msdn.microsoft.com/en-us/library/system.web.aspnethostingpermission.level.aspx)的值必须为“Unlimited”。  
  
-   从 Visual Studio 编辑器中拖动或粘贴的选定文本，如代码段。  
  
 工具箱无法显示的项包括：  
  
-   Excel 工作簿文件。  
  
-   共享网络服务器上安装的 .NET Framework 程序集。  
  
    > [!NOTE]
    >  从 UNC 路径添加的程序集不完全受信任，因此未向它授予足够的权限，无法显示在工具箱中。  
  
### 更正此错误  
  
1.  使用**“自定义工具箱”**对话框将本地计算机上安装的控件或组件添加到活动工具箱选项卡中。  
  
     \- 或 \-  
  
2.  将选定文本从 Visual Studio 编辑器拖动或粘贴到工具箱中。  
  
## 请参阅  
 [Choose Toolbox Items Dialog Box \(Visual Studio\)](http://msdn.microsoft.com/zh-cn/bd07835f-18a8-433e-bccc-7141f65263bb)   
 [How to: Manipulate Toolbox Tabs](http://msdn.microsoft.com/zh-cn/21285050-cadd-455a-b1f5-a2289a89c4db)   
 [工具箱](../Topic/Toolbox.md)