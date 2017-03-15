---
title: "错误 C1051 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C1051"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1051"
ms.assetid: 87dcbd3b-0952-499a-bd42-64f9e8de2605
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 错误 C1051
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

程序数据库文件“pdbfile”具有过时的格式，请将其删除并重新编译  
  
 编译器无法更新程序数据库文件，该文件的版本比较旧。  删除该文件并使用 **\/Zi** 或 **\/ZI** 重新编译程序。  有关更多信息，请参阅[\/Z7、\/Zi、\/ZI（调试信息格式）](../../build/reference/z7-zi-zi-debug-information-format.md)。