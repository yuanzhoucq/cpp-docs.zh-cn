---
title: "如何：实现 C# 的 lock 关键字 (C++/CLI) | Microsoft Docs"
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
  - "lock C# 关键字 [C++]"
  - "lock 语句"
ms.assetid: 436fe544-ffb7-49b9-9798-90794e9974de
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：实现 C# 的 lock 关键字 (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本主题将说明如何在 Visual C\+\+ 中实现 C\# `lock` 关键字。  有关详细信息，请参阅[“锁定”语句](../Topic/lock%20Statement%20\(C%23%20Reference\).md)。  
  
 还可以使用 C\+\+ 支持库中的 `lock` 类。  有关更多信息，请参见[同步（lock 类）](../dotnet/synchronization-lock-class.md)。  
  
## 示例  
  
```  
// CS_lock_in_CPP.cpp  
// compile with: /clr  
using namespace System::Threading;  
ref class Lock {  
   Object^ m_pObject;  
public:  
   Lock( Object ^ pObject ) : m_pObject( pObject ) {  
      Monitor::Enter( m_pObject );  
   }  
   ~Lock() {  
      Monitor::Exit( m_pObject );  
   }  
};  
  
ref struct LockHelper {  
   void DoSomething();  
};  
  
void LockHelper::DoSomething() {  
   // Note: Reference type with stack allocation semantics to provide   
   // deterministic finalization  
  
   Lock lock( this );     
   // LockHelper instance is locked  
}  
  
int main()  
{  
   LockHelper lockHelper;  
   lockHelper.DoSomething();  
   return 0;  
}  
```  
  
## 请参阅  
 [与其他 .NET 语言的互操作性](../dotnet/interoperability-with-other-dotnet-languages-cpp-cli.md)