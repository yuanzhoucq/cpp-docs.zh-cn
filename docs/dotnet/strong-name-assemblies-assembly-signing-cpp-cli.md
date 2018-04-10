---
title: 强名称程序集 （程序集签名） (C + + /cli CLI) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- assemblies [C++]
- signing assemblies
- .NET Framework [C++], assembly signing
- assemblies [C++], signing
- linker [C++], assembly signing
- strong-named assemblies [C++]
ms.assetid: c337cd3f-e5dd-4c6f-a1ad-437e85dba1cc
caps.latest.revision: 6
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 2099389131145838a70b579053c65698dbc3a857
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="strong-name-assemblies-assembly-signing-ccli"></a>强名称程序集（程序集签名）(C++/CLI)
本主题讨论如何可以对程序集，通常被称为对程序集赋予强名称签名。  
  
## <a name="remarks"></a>备注  
 当使用 Visual c + +，使用链接器选项以避免与程序集签名的 CLR 属性相关的问题程序集进行签名：  
  
-   <xref:System.Reflection.AssemblyDelaySignAttribute>  
  
-   <xref:System.Reflection.AssemblyKeyFileAttribute>  
  
-   <xref:System.Reflection.AssemblyKeyNameAttribute>  
  
 不使用的特性的原因包括密钥名称是在可能会带来安全风险，如果文件名称包含机密信息的程序集元数据可见的事实。 此外，由 Visual c + + 开发环境使用的生成过程将导致该程序集签名用如果 CLR 特性用于为程序集赋予强名称，然后运行程序集上的 mt.exe 之类的后续处理工具的密钥无效。  
  
 如果你在命令行上生成，链接器选项用于对程序集进行签名，然后运行后续处理工具 （如 mt.exe)，你将需要使用 sn.exe 程序集重新签名。 或者，可以生成和延迟为程序集签名后运行后续处理的工具，需要完成的签名。  
  
 如果你使用的签名的特性，在开发环境中生成时，可以通过显式调用 sn.exe 成功注册程序集 ([Sn.exe （强名称工具）](/dotnet/framework/tools/sn-exe-strong-name-tool)) 在生成后事件。 有关详细信息，请参阅[指定生成事件](../ide/specifying-build-events.md)。 如果你使用属性和生成后事件，相比于使用链接器选项，生成时间可能小于。  
  
 以下链接器选项支持签名的程序集：  
  
-   [/DELAYSIGN （部分程序集的签名）](../build/reference/delaysign-partially-sign-an-assembly.md)  
  
-   [/KEYFILE （指定密钥或密钥对程序集进行签名）](../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)  
  
-   [/KEYCONTAINER （指定密钥容器程序集进行签名）](../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md)  
  
 有关强的程序集的详细信息，请参阅[创建和使用具有强名称程序集](/dotnet/framework/app-domains/create-and-use-strong-named-assemblies)。  
  
## <a name="see-also"></a>请参阅  
 [使用 C++/CLI (Visual C++) 进行 .NET 编程](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)