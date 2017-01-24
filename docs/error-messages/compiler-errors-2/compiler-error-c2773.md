---
title: "编译器错误 C2773 | Microsoft Docs"
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
  - "C2773"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2773"
ms.assetid: 8d564b26-1623-4d92-aabc-dff33f7b1145
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2773
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

\#import 和 \#using 只在 C\+\+ 编译器中可用  
  
 C 编译器不能识别 `#import` 预处理器指令。  请使用 C\+\+ 编译该源。  如果需要的话，请使用 [\/Tp](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md)。