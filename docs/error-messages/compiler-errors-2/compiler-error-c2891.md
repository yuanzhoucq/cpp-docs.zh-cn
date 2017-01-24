---
title: "编译器错误 C2891 | Microsoft Docs"
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
  - "C2891"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2891"
ms.assetid: e12cfb2d-df45-4b0d-b155-c51d17e812fa
caps.latest.revision: 7
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2891
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“parameter”: 无法获取模板参数的地址  
  
 请不要使用以下代码：  
  
```  
template <int i> int* f() { return &i; }  
```  
  
 而改为使用：  
  
```  
template <int i> int* f() { return i; }  
```