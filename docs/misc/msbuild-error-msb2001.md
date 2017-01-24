---
title: "MSBuild 错误 MSB2001 | Microsoft Docs"
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
  - "MSBuild.MissingOldProjectFile"
helpviewer_keywords: 
  - "MSB2001"
ms.assetid: af3f4154-7ef3-4903-bde9-b18a66392622
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 错误 MSB2001
**元素 \<{0}\> 不包含必选特性“{1}”。**  
  
 正在进行转换的项目已被修改、损坏或者未由 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 创建。  
  
### 更正此错误  
  
-   检查项目文件是否已被修改或损坏。  如果项目已被修改或损坏，请用创建项目所用的 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 版本将项目打开，保存项目，然后尝试再次转换项目。  
  
## 请参阅  
 [Devenv 命令行开关](../Topic/Devenv%20Command%20Line%20Switches.md)   
 [命令行参考](../Topic/MSBuild%20Command-Line%20Reference.md)