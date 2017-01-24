---
title: "使用 ADO.NET 的数据访问 (C++/CLI) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - ".NET Framework [C++], 数据访问"
  - "ADO.NET [C++]"
  - "数据 [C++], ADO.NET"
  - "数据访问 [C++], ADO.NET"
  - "数据库 [C++], 在 C++ 中访问"
ms.assetid: b0cd987d-1ea7-4f76-ba01-cbd52503d06d
caps.latest.revision: 12
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 使用 ADO.NET 的数据访问 (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

ADO.NET 是用于数据访问的 .NET Framework API，它提供的强大功能和易用性是以前的数据访问解决方案所无法匹敌的。  此节描述一些只对 Visual C\+\+ 用户才会涉及的 ADO.NET 的问题，如封送处理本机类型。  
  
 ADO.NET 在公共语言运行时 \(CLR\) 下运行。  因此，与 ADO.NET 交互的任何应用程序也必须面向 CLR。  但是，这并不意味着本机应用程序不能使用 ADO.NET。  下列示例将说明如何从本机代码与 ADO.NET 数据库进行交互。  
  
## 本节内容  
 [如何：为 ADO.NET 封送 ANSI 字符串](../dotnet/how-to-marshal-ansi-strings-for-adonet-cpp-cli.md)  
  
 [如何：为 ADO.NET 封送 BSTR 字符串](../dotnet/how-to-marshal-bstr-strings-for-adonet-cpp-cli.md)  
  
 [如何：为 ADO.NET 封送 Unicode 字符串](../dotnet/how-to-marshal-unicode-strings-for-adonet-cpp-cli.md)  
  
 [如何：为 ADO.NET 封送 VARIANT](../dotnet/how-to-marshal-a-variant-for-adonet-cpp-cli.md)  
  
 [如何：为 ADO.NET 封送 SAFEARRAY](../dotnet/how-to-marshal-a-safearray-for-adonet-cpp-cli.md)  
  
## 相关章节  
  
|节|说明|  
|-------|--------|  
|[ADO.NET](../Topic/ADO.NET.md)|提供 ADO.NET 的概述，ADO.NET 是一组类，可向 .NET 程序员提供数据访问服务。|  
|[Creating SQL Server 2005 Objects In Managed Code](http://msdn.microsoft.com/zh-cn/5358a825-e19b-49aa-8214-674ce5fed1da)|介绍如何使用 .NET 语言（包括 Visual C\+\+）创建数据库对象，如存储过程、聚合、触发器、用户定义的函数和用户定义的类型，以及如何检索和更新 Microsoft SQL Server 2005 数据库数据。|  
  
## 请参阅  
 [使用 C\+\+\/CLI 进行 .NET 编程](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)   
 [本机和 .NET 的互操作性](../dotnet/native-and-dotnet-interoperability.md)