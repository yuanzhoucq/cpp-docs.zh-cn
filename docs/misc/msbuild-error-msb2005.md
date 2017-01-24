---
title: "MSBuild 错误 MSB2005 | Microsoft Docs"
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
  - "MSBuild.NoRootProjectElement"
helpviewer_keywords: 
  - "MSB2005"
ms.assetid: 62db2963-3811-4a92-8f4d-ff9145cb53ef
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 错误 MSB2005
**元素 \<{0}\> 不能包含特性。**  
  
 此错误信息中指定的元素不能包含特性。  
  
### 更正此错误  
  
-   从指定元素中删除特性。  
  
-   检查项目文件是否已被修改或损坏。  如果项目已被修改或损坏，请用创建项目所用的 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 版本将项目打开，保存项目，然后尝试再次转换项目。  
  
## 请参阅  
 [其他资源](../Topic/Additional%20MSBuild%20Resources.md)