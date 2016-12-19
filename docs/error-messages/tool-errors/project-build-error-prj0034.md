---
title: "项目生成错误 PRJ0034 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "PRJ0034"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PRJ0034"
ms.assetid: 1da4a55b-231b-4476-8545-6997628fbc00
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 项目生成错误 PRJ0034
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

项目级自定义生成步骤的“附加依赖项”属性包含“macro”（计算为“macro\_expansion”）。  
  
 项目的自定义生成步骤在其附加依赖项中包含错误，原因可能是宏计算问题。  该错误可能还意味着路径有格式错误，包含在文件路径中是非法的字符或字符组合。  
  
 若要解决该错误，请修复宏或修复路径说明。  计算出的路径是项目目录的绝对路径。