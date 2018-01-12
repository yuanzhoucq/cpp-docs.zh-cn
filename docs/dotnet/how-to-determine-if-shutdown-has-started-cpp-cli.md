---
title: "如何： 确定关闭是否已启动 (C + + /cli CLI) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- .NET Framework, shutdown
- shutdown
- termination
- applications [C++], shutdown
ms.assetid: a8d39731-dea8-4f0a-96b7-2a5de09b21d7
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 4d89fa475c997e0842ef9de5a21c26e664f25d78
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-determine-if-shutdown-has-started-ccli"></a>如何：确定关闭是否已启动 (C++/CLI)
下面的代码示例演示如何确定是否应用程序或.NET Framework 正在当前终止。 这可用于访问.NET Framework 中的静态元素，因为在关闭期间，这些构造由系统完成，并且不能可靠地使用。 通过检查<xref:System.Environment.HasShutdownStarted%2A>属性首先，你可以避免因无法访问这些元素的可能的故障。  
  
## <a name="example"></a>示例  
  
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
  
## <a name="see-also"></a>请参阅  
 [Windows 操作 (C + + /cli CLI)](../dotnet/windows-operations-cpp-cli.md)   
 [使用 C++/CLI (Visual C++) 进行 .NET 编程](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)