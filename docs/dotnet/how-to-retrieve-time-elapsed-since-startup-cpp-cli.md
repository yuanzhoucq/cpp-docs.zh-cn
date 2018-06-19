---
title: 如何： 自启动以来经过的检索时间 (C + + /cli CLI) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- time, elapsed since startup
- counters, elapsed time
- startup, time elapsed since
- tick counts
- startup
ms.assetid: a31fdecc-099e-4dd1-a176-f682289c5dd0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 4bebd086d24c741f0c5287e8a7fd0de6b535dfc6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33132825"
---
# <a name="how-to-retrieve-time-elapsed-since-startup-ccli"></a>如何：检索自启动以来经过的时间 (C++/CLI)
下面的代码示例演示如何确定滴答计数，或启动 Windows 后经过的毫秒数。 此值存储在<xref:System.Environment.TickCount%2A?displayProperty=fullName>成员，因为它是一个 32 位值，将重置为零大约每 24.9 天。  
  
## <a name="example"></a>示例  
  
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
  
## <a name="see-also"></a>请参阅  
 [Windows 操作 (C + + /cli CLI)](../dotnet/windows-operations-cpp-cli.md)   
 [使用 C++/CLI (Visual C++) 进行 .NET 编程](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)