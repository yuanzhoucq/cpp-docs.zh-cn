---
title: "项目生成错误 PRJ0036 | Microsoft Docs"
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
  - "PRJ0036"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PRJ0036"
ms.assetid: ee215cd1-2d66-474d-9a63-b9096f1c4923
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 项目生成错误 PRJ0036
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Web 部署工具的“附加文件”属性包含无效项。  
  
 Web 部署属性页上的“附加文件”属性包含错误，原因可能是宏计算问题。  该错误可能还意味着路径有格式错误，包含在文件路径中是非法的字符或字符组合。  
  
 若要解决该错误，请修复宏或修复路径说明。  计算出的路径是项目目录的绝对路径。  
  
 此错误还可意味着引用的其中一个文件不存在。