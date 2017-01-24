---
title: "Resources &#39;file1&#39; and &#39;file2&#39; have the same manifest resource name &#39;name&#39; | Microsoft Docs"
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
  - "vs.tasklisterror.resource_naming_conflict"
ms.assetid: 50d656ad-8557-4240-95b0-3f44b9c21da6
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Resources &#39;file1&#39; and &#39;file2&#39; have the same manifest resource name &#39;name&#39;
项目系统对两个文件进行计算，最终得出相同的程序集资源名称，这两个文件的 `BuildAction` 属性均被设置为 `EmbeddedResource`，且具有非特定区域性。  若发生此错误，则生成进程将会失败。  有关 `BuildAction` 属性的更多信息，请参见 [File Properties](http://msdn.microsoft.com/zh-cn/013c4aed-08d6-4dce-a124-ca807ca08959)。  
  
 由于 [!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 没有基于文件夹的命名空间的概念，因此如果资源文件名为：  
  
-   Proj1\\FolderA\\MyProj.bmp  
  
-   Proj1\\FolderB\\MyProj.bmp  
  
 将为两个文件都产生程序集清单名称 Proj1.MyProj.bmp。  
  
 **更正此错误**  
  
-   若要解决此错误，请重命名受影响的资源文件（*file1* 和 *file2*）。  
  
## 请参阅  
 [NIB: Resource File Naming Conventions](http://msdn.microsoft.com/zh-cn/7b1a2cdf-6196-4034-8fc7-51a271842cc2)