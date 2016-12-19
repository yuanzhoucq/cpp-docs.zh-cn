---
title: "未能将临时文件复制到输出目录中 | Microsoft Docs"
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
  - "vs.tasklisterror.cannot_copy_to_run_dir"
ms.assetid: b8b54984-74c9-4b9b-8164-d0d13c141055
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 未能将临时文件复制到输出目录中
项目系统无法将临时文件复制到输出目录。 编译器总是生成到中间目录，例如，obj\\`configname`。 在生成进程结束时，项目系统会将文件从中间目录复制到项目输出目录中。  
  
 当编译的某个程序集大于 64 KB 并且以下条件之一成立（或二者均成立）时，则可能会出现此问题：  
  
-   解决方案包含编译到同一输出文件夹中的项目。  
  
-   引用的程序集或项目之一的“复制本地”属性设置为 False。  
  
 **更正此错误**  
  
-   将各个项目的输出编译到不同的文件夹中。  
  
-   将引用的程序集或项目的“复制本地”属性设置为 True。  
  
-   确保没有打开“对象浏览器”窗口。  
  
-   确保没有在 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 的其他实例中打开相同的项目。  
  
## 请参阅  
 [NIB：如何：设置引用的“复制本地”属性](http://msdn.microsoft.com/zh-cn/dfe2ba13-f27f-4356-a481-ea67d5acacbd)