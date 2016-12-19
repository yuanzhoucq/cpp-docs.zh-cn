---
title: "如何：实现 C# 的 is 和 as 关键字 (C++/CLI) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "as C# 关键字 [C++]"
  - "is C# 关键字 [C++]"
ms.assetid: bc66c0d1-696b-480d-977c-5d9d1ad1ece6
caps.latest.revision: 15
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：实现 C# 的 is 和 as 关键字 (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本主题演示如何在 Visual C\+\+ 中实现 `is` 和 `as` C\# 关键字的功能。  
  
 有关更多信息，请参见[is](../Topic/is%20\(C%23%20Reference\).md)和[as](../Topic/as%20\(C%23%20Reference\).md)。  
  
## 示例  
  
```  
// CS_is_as.cpp  
// compile with: /clr  
using namespace System;  
  
interface class I {  
public:  
   void F();  
};  
  
ref struct C : public I {  
   virtual void F( void ) { }  
};  
  
template < class T, class U >   
Boolean isinst(U u) {  
   return dynamic_cast< T >(u) != nullptr;  
}  
  
int main() {  
   C ^ c = gcnew C();  
   I ^ i = safe_cast< I ^ >(c);   // is (maps to castclass in IL)  
   I ^ ii = dynamic_cast< I ^ >(c);   // as (maps to isinst in IL)  
  
   // simulate 'as':  
   Object ^ o = "f";  
   if ( isinst< String ^ >(o) )  
      Console::WriteLine("o is a string");  
}  
```  
  
  **o is a string**   
## 请参阅  
 [与其他 .NET 语言的互操作性](../dotnet/interoperability-with-other-dotnet-languages-cpp-cli.md)