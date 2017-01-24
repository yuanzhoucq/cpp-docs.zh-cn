---
title: "如何：使用可视化工具 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.dataviewer"
  - "vs.debug.stringviewer"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "调试器, 可视化工具"
  - "可视化工具, 关于可视化工具"
ms.assetid: d2611385-0134-4387-8c5a-979fe625a462
caps.latest.revision: 37
caps.handback.revision: 37
ms.author: "susanno"
manager: "douge"
---
# 如何：使用可视化工具
您可以使用可视化工具，以对变量或对象的数据类型有意义的方式来显示该变量或对象的内容。  您可以通过**“数据提示”**、**“监视”**窗口、**“自动”**窗口或**“局部变量”**窗口来使用可视化工具。  
  
 Compact Framework 上不支持可视化工具。  
  
> [!NOTE]
>  **存储**应用仅支持标准文本、HTML、XML 和 JSON 可视化工具。  不支持自定义（用户创建的）可视化工具。  
  
### 打开可视化工具  
  
1.  单击**“数据提示”**、**“监视”**窗口、**“自动”**或**“局部变量”**或**“快速监视”**窗口中变量名旁边显示的放大镜图标。  
  
     将会显示可视化工具列表。  
  
2.  单击要使用的可视化工具。  
  
### 在远程调试过程中对托管代码使用可视化工具  
  
-   首先将可视化工具 DLL 复制到远程计算机中，然后再启动调试会话。  
  
     远程计算机和本地计算机上的 DLL 路径必须相同。  此路径可为下列任一位置：  
  
     *Visual Studio 安装路径*`\Common7\Packages\Debugger\Visualizers`  
  
     \- 或 \-  
  
     `My Documents\Visual Studio 2010\Visualizers`*Visual Studio 版本*`\Visualizers`  
  
## 请参阅  
 [可视化工具](../Topic/Create%20Custom%20Visualizers%20of%20Data.md)   
 [如何：安装可视化工具](../Topic/How%20to:%20Install%20a%20Visualizer.md)   
 [如何：编写可视化工具](../Topic/How%20to:%20Write%20a%20Visualizer.md)   
 [查看数据提示中的数据值](../Topic/View%20data%20values%20in%20Data%20Tips%20%20in%20the%20code%20editor.md)