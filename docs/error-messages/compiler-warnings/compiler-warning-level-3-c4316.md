---
title: "编译器警告（等级 3）C4316 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4316"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4316"
ms.assetid: 10371f01-aeb8-40ac-a290-59e63efa5ad4
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# 编译器警告（等级 3）C4316
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

堆中分配的对象不会为此类型对齐。  
  
 使用 `operator new` 分配的过对齐对象可能没有指定的对齐方式。  为过对齐类型重写[运算符新](../../c-runtime-library/operator-new-crt.md)和[运算符删除](../../c-runtime-library/operator-delete-crt.md)，这样您可以使用对其的分配例程，例如 [\_aligned\_malloc](../../c-runtime-library/reference/aligned-malloc.md) 和 [\_aligned\_free](../../c-runtime-library/reference/aligned-free.md)。  下面的示例生成 C4316：  
  
```cpp  
// C4316.cpp  
// Test: cl /W3 /c C4316.cpp  
  
__declspec(align(32)) struct S {}; // C4324  
  
int main() {  
    new S; // C4316  
}  
```