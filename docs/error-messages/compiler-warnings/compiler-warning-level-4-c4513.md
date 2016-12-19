---
title: "编译器警告（等级 4）C4513 | Microsoft Docs"
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
  - "C4513"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4513"
ms.assetid: 6877334a-f30a-4184-9483-dac3348737a4
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 4）C4513
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“class”: 未能生成析构函数  
  
 编译器无法为给定的类生成默认析构函数；未创建任何析构函数。  包含析构函数的基类无法由派生类访问。  如果基类包含私有析构函数，使该析构函数成为公共的或受保护的。