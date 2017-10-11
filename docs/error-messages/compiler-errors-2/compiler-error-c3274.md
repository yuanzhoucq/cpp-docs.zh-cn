---
title: "编译器错误 C3274 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3274
dev_langs:
- C++
helpviewer_keywords:
- C3274
ms.assetid: 1f03f18e-b569-48eb-9249-11c70122a305
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 6fc2149b3aac1e3575500ed4ac6c3c1b283f1db4
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3274"></a>编译器错误 C3274
__finally/finally 没有匹配的 try  
  
 发现 [__finally](../../cpp/try-finally-statement.md) 或 [finally](../../dotnet/finally.md) 语句没有匹配的 `try`。 若要解决此问题，删除 `__finally` 语句或为 `try` 添加 `__finally`语句。  
  
 以下示例生成 C3274：  
  
```  
// C3274.cpp  
// compile with: /clr  
// C3274 expected  
using namespace System;  
int main() {  
   try {  
      try {  
         throw gcnew ApplicationException();  
      }  
      catch(...) {  
         Console::Error->WriteLine(L"Caught an exception");  
      }  
      finally {  
         Console::WriteLine(L"In finally");  
      }  
   } finally {  
      Console::WriteLine(L"In finally");  
   }  
  
   // Uncomment the following 3 lines to resolve.  
   // try {  
   //   throw gcnew ApplicationException();  
   // }  
  
   finally {  
      Console::WriteLine(L"In finally");  
   }  
   Console::WriteLine(L"**FAIL**");  
}  
```
