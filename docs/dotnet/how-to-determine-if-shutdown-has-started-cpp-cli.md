---
title: "如何：确定关闭是否已启动 (C++/CLI) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".NET Framework, 关机"
  - "应用程序 [C++], 关机"
  - "关机"
  - "终止"
ms.assetid: a8d39731-dea8-4f0a-96b7-2a5de09b21d7
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：确定关闭是否已启动 (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下面的代码示例演示如何确定应用程序或 .NET Framework 当前是否正在终止。  这对于访问 .NET Framework 中的静态元素非常有用，因为在关闭期间，这些构造将由系统完成，并且不能可靠地进行使用。  通过首先检查 <xref:System.Environment.HasShutdownStarted%2A> 属性，可避免因无法访问这些元素而可能导致的故障。  
  
## 示例  
  
```  
// check_shutdown.cpp  
// compile with: /clr  
using namespace System;  
int main()   
{  
   if (Environment::HasShutdownStarted)  
      Console::WriteLine("Shutting down.");  
   else  
      Console::WriteLine("Not shutting down.");  
   return 0;  
}  
```  
  
## 请参阅  
 [Windows 操作](../dotnet/windows-operations-cpp-cli.md)   
 [使用 C\+\+\/CLI 进行 .NET 编程](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)