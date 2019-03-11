---
title: 强名称程序集（程序集签名）(C++/CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- assemblies [C++]
- signing assemblies
- .NET Framework [C++], assembly signing
- assemblies [C++], signing
- linker [C++], assembly signing
- strong-named assemblies [C++]
ms.assetid: c337cd3f-e5dd-4c6f-a1ad-437e85dba1cc
ms.openlocfilehash: 762c95c3ecc60995e8d0e6f9e4f7bc95d179c26f
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/11/2019
ms.locfileid: "57747496"
---
# <a name="strong-name-assemblies-assembly-signing-ccli"></a>强名称程序集（程序集签名）(C++/CLI)

本主题讨论如何对您的程序集，通常被称为对程序集赋予强名称签名。

## <a name="remarks"></a>备注

当使用 Visual c + +，使用链接器选项以避免与程序集签名的 CLR 属性相关的问题在程序集进行签名：

- <xref:System.Reflection.AssemblyDelaySignAttribute>

- <xref:System.Reflection.AssemblyKeyFileAttribute>

- <xref:System.Reflection.AssemblyKeyNameAttribute>

不使用属性的原因包括密钥的名称将显示在程序集元数据，可能会有安全风险，如果文件名称中包含机密信息的事实。 此外，使用由 Visual c + + 开发环境的生成过程将导致与该程序集已签名，如果你使用 CLR 属性来为程序集赋予强名称，然后运行程序集上 mt.exe 之类的后续处理工具的密钥无效。

如果你在命令行生成、 链接器选项用于对程序集签名，然后运行后续处理工具 （如 mt.exe)，您需要使用 sn.exe 程序集重新签名。 或者，可以生成和延迟签名程序集并后运行后续处理的工具，需要完成的签名。

如果在开发环境中生成时使用的签名特性，可以通过显式调用 sn.exe 成功登录该程序集 ([Sn.exe （强名称工具）](/dotnet/framework/tools/sn-exe-strong-name-tool)) 后期生成事件中。 有关详细信息，请参阅[指定生成事件](../ide/specifying-build-events.md)。 如果使用属性和生成后事件，与使用链接器选项相比，生成时间可能会更少。

以下链接器选项支持程序集签名：

- [/DELAYSIGN（为程序集进行部分签名）](../build/reference/delaysign-partially-sign-an-assembly.md)

- [/KEYFILE（指定密钥或密钥对以便为程序集签名）](../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)

- [/KEYCONTAINER（指定密钥容器以便为程序集签名）](../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md)

有关强的程序集的详细信息，请参阅[创建和使用具有强名称程序集](/dotnet/framework/app-domains/create-and-use-strong-named-assemblies)。

## <a name="see-also"></a>请参阅

[使用 C++/CLI (Visual C++) 进行 .NET 编程](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)
