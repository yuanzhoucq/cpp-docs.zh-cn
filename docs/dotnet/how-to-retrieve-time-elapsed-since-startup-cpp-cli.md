---
title: "如何：检索自启动以来经过的时间 (C++/CLI) | Microsoft Docs"
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
  - "计数器, 运行时间"
  - "启动"
  - "启动, 运行时间自"
  - "刻度计数"
  - "时间, 自启动后已运行的"
ms.assetid: a31fdecc-099e-4dd1-a176-f682289c5dd0
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：检索自启动以来经过的时间 (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下面的代码示例演示如何确定刻度计数，或自 Windows 启动以来已经流逝的毫秒数。  此值存储在 <xref:System.Environment.TickCount%2A?displayProperty=fullName> 成员中，并且由于该值为 32 位值，因此大约每 24.9 天就会重置为零。  
  
## 示例  
  
```  
// startup_time.cpp  
// compile with: /clr  
using namespace System;  
  
int main( )   
{  
   Int32 tc = Environment::TickCount;  
   Int32 seconds = tc / 1000;  
   Int32 minutes = seconds / 60;  
   float hours = static_cast<float>(minutes) / 60;  
   float days = hours / 24;  
  
   Console::WriteLine("Milliseconds since startup: {0}", tc);  
   Console::WriteLine("Seconds since startup: {0}", seconds);  
   Console::WriteLine("Minutes since startup: {0}", minutes);  
   Console::WriteLine("Hours since startup: {0}", hours);  
   Console::WriteLine("Days since startup: {0}", days);  
  
   return 0;  
}  
```  
  
## 请参阅  
 [Windows 操作](../dotnet/windows-operations-cpp-cli.md)   
 [使用 C\+\+\/CLI 进行 .NET 编程](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)