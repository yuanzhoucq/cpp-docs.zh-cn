---
title: "编译器错误 C2348 | Microsoft Docs"
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
  - "C2348"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2348"
ms.assetid: 4c4d701f-ccf1-46fe-9ddb-3f341684f269
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2348
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“type name”: 不是 C 样式的聚合，无法在嵌入的 IDL 中导出  
  
 若要使用 [export](../../windows/export.md) 特性将 `struct` 放在 .idl 文件中，`struct` 必须只含有数据。  
  
 下面的示例生成 C2348：  
  
```  
// C2348.cpp  
// C2348 error expected  
[ module(name="SimpleMidlTest") ];  
  
[export]  
struct Point {  
   // Delete the following two lines to resolve.  
   Point() : m_i(0), m_j(0) {}  
   Point(int i, int j) : m_i(i), m_j(j) {}  
  
   int m_i;  
   int m_j;  
};  
```