---
title: "强名称程序集（程序集签名）(C++/CLI) | Microsoft Docs"
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
  - ".NET Framework [C++], 程序集签名"
  - "程序集 [C++]"
  - "程序集 [C++], 签名"
  - "链接器 [C++], 程序集签名"
  - "对程序集进行签名"
  - "具有强名称的程序集 [C++]"
ms.assetid: c337cd3f-e5dd-4c6f-a1ad-437e85dba1cc
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 强名称程序集（程序集签名）(C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本主题讨论如何对程序集签名，也经常称为对程序集赋予一个强名称。  
  
## 备注  
 当使用 Visual C\+\+ 时，请使用链接器选项对程序集签名，以免出现与程序集签名的 CLR 特性相关的问题：  
  
-   <xref:System.Reflection.AssemblyDelaySignAttribute>  
  
-   <xref:System.Reflection.AssemblyKeyFileAttribute>  
  
-   <xref:System.Reflection.AssemblyKeyNameAttribute>  
  
 不使用特性的原因包括密钥名称在程序集元数据中是可见的这一事实，如果文件名包括机密信息，这将导致安全风险。  此外，如果使用 CLR 特性为程序集赋予一个强名称，然后在该程序集上运行 mt.exe 这样的后续处理工具，则 Visual C\+\+ 开发环境使用的生成过程将导致对程序集签名所用的密钥无效。  
  
 如果通过命令行生成，并使用链接器选项对程序集签名，然后运行后期处理工具（如 mt.exe），则需要使用 sn.exe 重新为程序集签名。  或者，您可以生成程序集并延迟签名，在运行后期处理工具后再完成签名。  
  
 如果在开发环境中生成项目时使用签名特性，则可以通过在生成后事件中显式调用 sn.exe \([Sn.exe（强名称工具）](../Topic/Sn.exe%20\(Strong%20Name%20Tool\).md)\) 来成功地对程序集进行签名。  有关详细信息，请参阅[指定生成事件](../ide/specifying-build-events.md)。  如果您使用特性和生成后事件，则生成所需的时间会比使用链接器选项时短。  
  
 以下链接器选项支持程序集签名：  
  
-   [\/DELAYSIGN（为程序集进行部分签名）](../build/reference/delaysign-partially-sign-an-assembly.md)  
  
-   [\/KEYFILE（指定密钥或密钥对以便为程序集签名）](../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)  
  
-   [\/KEYCONTAINER（指定密钥容器以便为程序集签名）](../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md)  
  
 有关强程序集的更多信息，请参见 [创建和使用具有强名称的程序集](../Topic/Creating%20and%20Using%20Strong-Named%20Assemblies.md)。  
  
## 请参阅  
 [使用 C\+\+\/CLI 进行 .NET 编程](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)