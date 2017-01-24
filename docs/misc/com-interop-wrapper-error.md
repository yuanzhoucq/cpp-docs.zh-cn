---
title: "COM Interop Wrapper Error | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.cannotcopyassembly"
  - "Vs.refruntlbimp"
helpviewer_keywords: 
  - "COM Interop Wrapper dialog box"
ms.assetid: 9a9d6374-ee26-4dbc-9e34-e1d90f6254b4
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# COM Interop Wrapper Error
当项目系统无法创建针对特定组件的 COM 互操作包装时，将显示此消息框。  COM 互操作包装是公共语言运行时 \(CLR\) 所需要用来管理和与 COM 组件进行通信。  有关详细信息，请参阅 [Visual Basic 和 Visual C\# 中的 COM 互操作性](../Topic/COM%20Interoperability%20in%20.NET%20Framework%20Applications%20\(Visual%20Basic\).md)。  
  
 问题的常见原因包括：  
  
-   未正确注册该组件的类型库。  
  
-   计算机上找不到正在包装的组件所依赖的组件。  
  
 在这两种情况下，你需确保的计算机上正确安装并注册 COM 组件，然后重试该操作。  
  
> [!TIP]
>  您还可以搜索 [MSDN 网站](http://go.microsoft.com/fwlink/?LinkId=3355)，了解为你特定的 COM 组件发布的 COM 互操作包装。  
  
> [!NOTE]
>  COM 互操作包装有时被称为“主互操作程序集”。 它们表达的都是同一个意思  
  
## 请参阅  
 [Visual Studio 中的组件模型命名空间](http://msdn.microsoft.com/zh-cn/705d0add-0707-44ba-a6de-637381d9c937)   
 [组件创作](../Topic/Component%20Authoring.md)   
 [COM 互操作](../Topic/COM%20Interop%20\(Visual%20Basic\).md)   
 [公共语言运行时](../Topic/Common%20Language%20Runtime%20\(CLR\).md)   
 [.NET Framework 应用程序中的 COM 互操作性](../Topic/COM%20Interoperability%20in%20.NET%20Framework%20Applications%20\(Visual%20Basic\).md)