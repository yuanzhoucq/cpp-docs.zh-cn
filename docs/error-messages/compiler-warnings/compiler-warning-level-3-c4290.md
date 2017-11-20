---
title: "编译器警告 （等级 3） C4290 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4290
dev_langs: C++
helpviewer_keywords: C4290
ms.assetid: d1c6d85b-28e0-4a1f-9d48-23593337a6fb
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ccf7fee7cafb771f669a4d8730fed7c6c323c3c7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-3-c4290"></a>编译器警告（等级 3）C4290
C + + 异常规范忽略除指示函数不是 __declspec （nothrow）  
  
 使用异常规范，Visual c + + 接受，但不实现声明的函数。 代码与异常在编译过程中忽略的规范可能需要重新编译和链接要重复使用在将来版本支持异常规范。  
  
 有关详细信息，请参阅[异常规范 (throw)](../../cpp/exception-specifications-throw-cpp.md) 。  
  
 你可以通过使用来避免此警告[警告](../../preprocessor/warning.md)杂注：  
  
```  
#pragma warning( disable : 4290 )  
```  
  
 下面的代码示例生成 C4290:  
  
```  
// C4290.cpp  
// compile with: /EHs /W3 /c  
void f1(void) throw(int) {}   // C4290  
  
// OK  
void f2(void) throw() {}  
void f3(void) throw(...) {}  
```