---
title: "混合、 纯代码和可验证功能比较 (C + + /cli CLI) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- safe assemblies [C++], vs. pure
- mixed assemblies [C++], vs. pure
- safe assemblies [C++], vs. mixed
- pure MSIL [C++]
- verifiable assemblies [C++]
- pure MSIL [C++], vs. safe
- pure MSIL [C++], vs. mixed
- pure MSIL [C++], compared to mixed and safe
- verifiable assemblies [C++], vs. mixed
- mixed assemblies [C++], vs. safe
- verifiable assemblies [C++], vs. pure
- pure assemblies [C++]
- safe assemblies [C++]
- mixed assemblies [C++]
ms.assetid: 3f7a82ba-0e69-4927-ba0c-fbc3160e4394
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 3ee9fbed3fd82fd450fd179683fd119cb1630034
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="mixed-pure-and-verifiable-feature-comparison-ccli"></a>混合、纯 MSIL 和可验证编译模式的功能比较 (C++/CLI)
本主题将比较了不同的功能**/clr**编译模式。 有关详细信息，请参阅 [/clr（公共语言运行时编译）](../build/reference/clr-common-language-runtime-compilation.md)。  
  
 **/clr:pure** 和 **/clr:safe** 编译器选项在 Visual Studio 2015 中已弃用。  
  
## <a name="feature-comparison"></a>功能比较  
  
|功能|混合 (/ clr)|纯 (/ clr： 纯)|安全 (/: safe)|相关的信息|  
|-------------|---------------------|-------------------------|-------------------------|-------------------------|  
|CRT 库|支持|支持||[按类别分的运行时例程](../c-runtime-library/run-time-routines-by-category.md)|  
|MFC/ATL|支持|||[MFC 桌面应用程序](../mfc/mfc-desktop-applications.md)&#124;[类概述](../atl/atl-class-overview.md)|  
|非托管的函数|支持|||[混合（本机和托管）程序集](../dotnet/mixed-native-and-managed-assemblies.md)|  
|非托管的数据|支持|支持||[纯代码和可验证代码 (C++/CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md)|  
|可从非托管函数调用|支持|||[如何： 迁移到 /clr: pure (C + + /cli CLI)](../dotnet/how-to-migrate-to-clr-pure-cpp-cli.md)|  
|调用非托管的函数的支持|支持|仅限 C 样式函数|P/Invoke 仅|[使用 C++ 互操作（隐式 PInvoke）](../dotnet/using-cpp-interop-implicit-pinvoke.md)|  
|支持反射|仅 Dll|支持|支持|[反射 (C++/CLI)](../dotnet/reflection-cpp-cli.md)|  
  
## <a name="see-also"></a>请参阅  
 [纯代码和可验证代码 (C++/CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md)