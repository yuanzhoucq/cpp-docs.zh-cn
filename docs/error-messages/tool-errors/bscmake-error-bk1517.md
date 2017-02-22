---
title: "BSCMAKE 错误 BK1517 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "BK1517"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BK1517"
ms.assetid: 24391f42-0a3e-40a9-9991-c8b9a6a7b1c7
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# BSCMAKE 错误 BK1517
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

同时用 \/Yc 和 \/Yu 编译的 sbrfile 的源文件  
  
 此 .sbr 文件引用自身。  可能在用 \/Yc 编译此文件后又用 \/Yu 重新编译了它。  重新将源文件的编译器选项设置为 \/Yc，然后选择“重新生成”生成新的 .sbr 文件。  不要用 \/Yu 重新编译源文件。