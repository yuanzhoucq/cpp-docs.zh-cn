---
title: "编译器警告（等级 2）C4826 | Microsoft Docs"
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
  - "C4826"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4826"
ms.assetid: 286f5c1d-8c14-43f7-aaa6-a891db2fdc64
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 2）C4826
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

从“type1”到“type\_2”的转换带有符号扩展。这可能导致意外的运行时行为。  
  
 此警告指示，将 32 位指针强制转换为 64 位变量时，编译器执行了符号扩展。  
  
 如果对 Windows HANDLE 类型执行了此扩展，则忽略此警告是安全的。  如果对指针类型执行了此扩展，则应修改强制转换，以阻止此符号扩展（请参见下例）。  
  
 默认情况下，C4826 处于关闭状态。  有关更多信息，请参见[默认情况下处于关闭状态的编译器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。  
  
## 示例  
 下面的示例生成 C4826。  
  
```  
// C4826.cpp  
// compile with: /W2 /c  
#include <windows.h>  
#pragma warning(default: 4826)  
  
void * __ptr64 F1 (void * __ptr32 P ) {  
   return (void * __ptr64)P;   // C4826  
   // try the following line instead  
   // return (void * __ptr64)(ULONGLONG)(ULONG)P;  
}  
  
void * __ptr64 F2 ( void * P ) {  
   return (void * __ptr64)P;   // C4826  
   // try the following line instead  
   // return (void * __ptr64)(ULONGLONG)(ULONG)P;  
}  
  
unsigned __int64 F3r ( void * P ) {  
   return (unsigned __int64)P;   // C4826  
   // try the following line instead  
   // return (unsigned __int64)(ULONGLONG)(ULONG)P;  
}  
```