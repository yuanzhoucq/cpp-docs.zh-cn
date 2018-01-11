---
title: "如何： 创建可验证的 c + + 项目 (C + + /cli CLI) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- verifiable assemblies [C++], creating
- conversions, C++ projects
- Visual C++ projects
ms.assetid: 4ef2cc1a-e3e5-4d67-8d8d-9c614f8ec5d3
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 4d6a7806183766d96c0d106d9d9e890b046f4563
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-create-verifiable-c-projects-ccli"></a>如何：创建可验证的 C++ 项目 (C++/CLI)
Visual c + + 应用程序向导不创建可验证项目中，但项目转换为可验证。 本主题介绍如何设置项目属性和修改项目源代码文件，以转换你的 Visual c + + 项目，以便生成可验证的应用程序。  
  
## <a name="compiler-and-linker-settings"></a>编译器和链接器设置  
 默认情况下，.NET 项目使用 /clr 编译器标志，并配置到面向 x86 硬件链接器。 对于可验证代码，你必须使用 /clr: safe 标志，并且你必须指示链接器生成 MSIL，而不是本机指令。  
  
#### <a name="to-change-the-compiler-and-linker-settings"></a>若要更改的编译器和链接器设置  
  
1.  显示项目属性页。 有关详细信息，请参阅[使用项目属性](../ide/working-with-project-properties.md)。  
  
2.  上**常规**下页上**配置属性**节点，设置**公共语言运行时支持**属性**安全 MSIL 公共语言运行时支持 (/: safe)**。  
  
3.  上**高级**下页上**链接器**节点，设置**CLR 映像类型**属性**强制安全 IL 映像 (/ CLRIMAGETYPE:SAFE)**。  
  
## <a name="removing-native-data-types"></a>删除本机数据类型  
 因为即使实际上并不用于非可验证本机数据类型，你必须删除包含本机类型的所有标头文件。  
  
> [!NOTE]
>  以下过程适用于 Windows 窗体应用程序 (.NET) 和控制台应用程序 (.NET) 的项目。  
  
#### <a name="to-remove-references-to-native-data-types"></a>若要删除对本机数据类型的引用  
  
1.  注释掉 Stdafx.h 文件中的所有内容。  
  
## <a name="configuring-an-entry-point"></a>配置入口点  
 由于可验证应用程序不能使用 C 运行时库 (CRT)，因此它们不能依赖于 CRT 来调用作为标准的入口点的主函数。 这意味着，你必须显式提供到链接器最初调用的函数的名称。 （在这种情况下，main （） 用于而不是 main （） 或 _tmain() 指示非 CRT 入口点，但必须显式指定的入口点，因为此名称是任意。）  
  
> [!NOTE]
>  以下过程适用于控制台应用程序 (.NET) 项目。  
  
#### <a name="to-configure-an-entry-point"></a>若要配置的入口点  
  
1.  将 _tmain() 更改为项目的主.cpp 文件中的 main （）。  
  
2.  显示项目属性页。 有关详细信息，请参阅[使用项目属性](../ide/working-with-project-properties.md)。  
  
3.  上**高级**下页上**链接器**节点，输入`Main`作为**入口点**属性值。  
  
## <a name="see-also"></a>请参阅  
 [纯代码和可验证代码 (C++/CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md)