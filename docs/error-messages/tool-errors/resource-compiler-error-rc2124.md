---
title: "资源编译器错误 RC2124 | Microsoft Docs"
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
  - "RC2124"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RC2124"
ms.assetid: 4eb5c4ec-ca9b-46a0-805b-35e040e9ed41
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 资源编译器错误 RC2124
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

不允许空菜单  
  
 在 **MENU** 语句中定义的任何菜单项之前有 **END** 关键字。  资源编译器不允许空菜单。  确保在 **MENU** 语句内没有任何左引号。