---
title: "编译器警告（等级 1）C4659 | Microsoft Docs"
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
  - "C4659"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4659"
ms.assetid: e29ba8db-7917-43f6-8e34-868b752279ae
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 1）C4659
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

\#pragma“pragma”: 使用的保留段“segment”有未定义的行为，使用 \#pragma comment\(linker, ...\)  
  
 错误地用 .drectve 选项向链接器传递选项。  应改用杂注 [comment](../../preprocessor/comment-c-cpp.md) 传递链接器选项。  
  
```  
// C4659.cpp  
// compile with: /W1 /LD  
#pragma code_seg(".drectve")   // C4659  
```