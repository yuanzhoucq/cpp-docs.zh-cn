---
title: "无法将多文件程序集组件“component_filename”复制到文件“destination_filename”。 &lt;reason.&gt; | Microsoft Docs"
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
  - "vs.tasklisterror.cannotcopyscattercomponent"
ms.assetid: 22f851fc-431b-4cdf-9de1-3a29727fa1e6
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 无法将多文件程序集组件“component_filename”复制到文件“destination_filename”。 &lt;reason.&gt;
指定的组件未复制到 bin 目录。  
  
 某些程序集由多个文件组成。 每当无法将属于多文件程序集的文件复制到运行目录时，将显示此诊断信息。  
  
 失败的原因有多种。 例如，磁盘空间不足，或达到路径长度的 MAX\_PATH 限制。 此外，某个过程（也许是 Visual Studio）占用了无法复制的组件。  
  
 **更正此错误**  
  
-   检查是否有足够的可用磁盘空间。  
  
-   尝试将项目移到其路径长度小于当前项目文件夹路径长度的文件夹。  
  
-   将输出目录更改为绝对路径长度较小的文件夹。 这仅适用于客户端（非 Web）项目。  
  
-   重新启动 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]。  
  
## 请参阅  
 [调试 Web 应用程序：错误和疑难解答](../Topic/Debugging%20Web%20Applications:%20Errors%20and%20Troubleshooting.md)