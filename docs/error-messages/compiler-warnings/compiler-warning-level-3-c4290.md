---
title: "编译器警告（等级 3）C4290 | Microsoft Docs"
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
  - "C4290"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4290"
ms.assetid: d1c6d85b-28e0-4a1f-9d48-23593337a6fb
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 3）C4290
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

忽略 C\+\+ 异常规范，但指示函数不是 \_\_declspec\(nothrow\)  
  
 使用异常规范声明函数，Visual C\+\+ 接受但并不实现此规范。  包含在编译期间被忽略的异常规范的代码可能需要重新编译和链接，以便在支持异常规范的未来版本中重用。  
  
 有关更多信息，请参见[异常规范 \(throw\)](../../cpp/exception-specifications-throw-cpp.md)。  
  
 使用 [warning](../../preprocessor/warning.md) 杂注可避免出现此警告：  
  
```  
#pragma warning( disable : 4290 )  
```  
  
 下面的代码示例生成 C4290：  
  
```  
// C4290.cpp  
// compile with: /EHs /W3 /c  
void f1(void) throw(int) {}   // C4290  
  
// OK  
void f2(void) throw() {}  
void f3(void) throw(...) {}  
```