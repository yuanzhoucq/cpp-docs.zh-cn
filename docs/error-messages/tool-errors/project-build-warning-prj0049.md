---
title: "项目生成警告 PRJ0049 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PRJ0049"
ms.assetid: 8b38afa1-e080-4efd-ae89-776cfd044413
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 项目生成警告 PRJ0049
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

引用的目标\<Reference”\>'要求 .NET Framework  \<MinFrameworkVersion\>且在此项目的目标 Framework 上将无法运行  
  
 使用 [!INCLUDE[vs_orcas_long](../../atl/reference/includes/vs_orcas_long_md.md)] 创建的应用程序可以指定它们应针对的 [!INCLUDE[dnprdnshort](../Token/dnprdnshort_md.md)] 版本。  如果添加对依赖比目标版本更新的 [!INCLUDE[dnprdnshort](../Token/dnprdnshort_md.md)] 版本的程序集或项目的引用，则在编译时将会出现此警告。  
  
### 更正此警告  
  
1.  选择以下选项之一：  
  
    -   更改项目的**“属性页”**对话框中的目标 Framework，以使其比所有引用的程序集和项目的最低 Framework 版本更新或相同。  有关详细信息，请参阅[添加引用](../../ide/adding-references-in-visual-cpp-projects.md)。  
  
    -   移除对其最低 Framework 版本比目标 Framework 更新的程序集或项目的引用。  这些项目在**“属性页”**中会用警告图标标记出来。  
  
## 请参阅  
 [项目生成错误和警告 \(PRJxxxx\)](../../error-messages/tool-errors/project-build-errors-and-warnings-prjxxxx.md)