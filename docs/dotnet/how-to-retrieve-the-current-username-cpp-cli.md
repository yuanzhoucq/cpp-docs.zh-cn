---
title: "如何：检索当前用户名 (C++/CLI) | Microsoft Docs"
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
  - "当前用户名"
  - "用户名, 检索"
  - "UserName 字符串"
ms.assetid: 91679571-d029-41f5-b657-1460c81c608a
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：检索当前用户名 (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下面的代码示例演示如何检索当前用户名（已登录到 Windows 的用户的名称）。  该名称存储在 <xref:System.Environment.UserName%2A> 字符串（在 <xref:System.Environment> 命名空间中定义）中。  
  
## 示例  
  
```  
// username.cpp  
// compile with: /clr  
using namespace System;  
  
int main()   
{  
   Console::WriteLine("\nCurrent user: {0}", Environment::UserName);  
   return 0;  
}  
```  
  
## 请参阅  
 [Windows 操作](../dotnet/windows-operations-cpp-cli.md)   
 [使用 C\+\+\/CLI 进行 .NET 编程](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)