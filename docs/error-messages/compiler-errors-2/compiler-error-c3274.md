---
title: "编译器错误 C3274 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3274"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3274"
ms.assetid: 1f03f18e-b569-48eb-9249-11c70122a305
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# 编译器错误 C3274
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

\_\_finally\/finally 没有匹配的 try  
  
 发现 [\_\_finally](../../cpp/try-finally-statement.md) 或 [finally](../../dotnet/finally.md) 语句没有匹配的 `try`。 若要解决此问题，删除 `__finally` 语句或为 `__finally` 添加 `try` 语句。  
  
 以下示例生成 C3274：  
  
```  
// C3274.cpp // compile with: /clr // C3274 expected using namespace System; int main() { try { try { throw gcnew ApplicationException(); } catch(...) { Console::Error->WriteLine(L"Caught an exception"); } finally { Console::WriteLine(L"In finally"); } } finally { Console::WriteLine(L"In finally"); } // Uncomment the following 3 lines to resolve. // try { //   throw gcnew ApplicationException(); // } finally { Console::WriteLine(L"In finally"); } Console::WriteLine(L"**FAIL**"); }  
```