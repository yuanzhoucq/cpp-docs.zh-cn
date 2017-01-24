---
title: "编译器错误 C2341 | Microsoft Docs"
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
  - "C2341"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2341"
ms.assetid: aa2a7da5-e1c8-4225-9939-5bdc50158f31
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2341
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“section name”: 使用段之前必须用 \#pragma data\_seg、code\_seg 或节进行定义  
  
 [allocate](../../cpp/allocate.md) 语句引用了 [code\_seg](../../preprocessor/code-seg.md)、[data\_seg](../../preprocessor/data-seg.md) 或 [section](../../preprocessor/section.md) 杂注尚未定义的段。  
  
 下面的示例生成 C2341：  
  
```  
// C2341.cpp  
// compile with: /c  
__declspec(allocate(".test"))   // C2341  
int j = 1;  
```  
  
 可能的解决方案：  
  
```  
// C2341b.cpp  
// compile with: /c  
#pragma data_seg(".test")  
__declspec(allocate(".test"))  
int j = 1;  
```