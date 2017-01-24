---
title: "编译器警告（等级 1）C4651 | Microsoft Docs"
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
  - "C4651"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4651"
ms.assetid: f1ea82aa-4dc1-4972-b55a-57fdb962f0dd
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 1）C4651
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

为预编译头，而非为当前编译指定“definition”  
  
 定义是在生成预编译头时指定的，而不是在此编译中指定的。  
  
 定义将在预编译头内部有效，而在代码的其余部分则无效。  
  
 如果预编译头是用 \/DSYMBOL 生成的，而 \/Yu 编译又不具有 \/DSYMBOL，这时编译器就会生成此警告。在 \/Yu 命令行中添加 \/DSYMBOL 便可消除此警告。