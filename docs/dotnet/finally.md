---
title: "finally | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "finally 关键字 [C++]"
ms.assetid: b55f3c8e-1af0-43e8-bcfb-99c3685d2578
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# finally
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

除了 `try` 和 `catch` 子句外，CLR 异常处理支持 `finally` 子句。  语义与在结构化异常处理块 \(SEH\) 的 `__finally` 相同。  `__finally` 块可以遵循 `try` 或 `catch` 块。  
  
## 备注  
 `finally` 块的目的将清理在异常发生后的所有资源。  请注意，`finally` 块总是执行，即使有异常未引发。  如果托管异常关联在 `try` 块内，引发 `catch` 块只执行。  
  
 `finally` 为区分上下文的关键字；请参见 [上下文相关的关键字](../windows/context-sensitive-keywords-cpp-component-extensions.md)。  
  
## 示例  
 下面的示例演示一个简单的 `finally` 块：  
  
```  
// keyword__finally.cpp  
// compile with: /clr  
using namespace System;  
  
ref class MyException: public System::Exception{};  
  
void ThrowMyException() {  
   throw gcnew MyException;  
}  
  
int main() {  
   try {  
      ThrowMyException();  
   }  
   catch ( MyException^ e ) {  
      Console::WriteLine(  "in catch" );  
      Console::WriteLine( e->GetType() );  
   }  
   finally {  
      Console::WriteLine(  "in finally" );  
   }  
}  
```  
  
  **在执行 catch**  
**MyException**  
**在最后**   
## 请参阅  
 [异常处理](../windows/exception-handling-cpp-component-extensions.md)