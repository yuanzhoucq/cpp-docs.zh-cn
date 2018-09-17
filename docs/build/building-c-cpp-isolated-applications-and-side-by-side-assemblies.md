---
title: 生成 C/c + + 独立应用程序和通过并行程序集 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- isolated applications [C++]
- WinSxS [C++]
- native assembly cache [C++]
- builds [C++], isolated applications
- side-by-side applications [C++]
- builds [C++], side-by-side assemblies
ms.assetid: 9465904e-76f7-48bd-bb3f-c55d8f1699b6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3b3327f4d0ae20b13c97ea0916e7a2c86e7006dd
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45710094"
---
# <a name="building-cc-isolated-applications-and-side-by-side-assemblies"></a>生成 C/C++ 独立应用程序和并行程序集

Visual c + + 的理论基础是 Windows 客户端应用程序支持的部署模型[独立应用程序](/windows/desktop/SbsCs/isolated-applications)并[通过并行程序集](/windows/desktop/SbsCs/about-side-by-side-assemblies-)。 默认情况下，Visual c + + 生成的所有本机 C/c + + 应用程序作为独立的应用程序使用[清单](https://msdn.microsoft.com/library/aa375365)来描述其在 Visual c + + 库上的依赖关系。

将 C/C++ 程序生成为独立应用程序具有一系列的好处。 例如，当其他 C/C++ 应用程序安装或卸载 Visual C++ 库时，不会影响独立应用程序。 独立应用程序使用的 visual c + + 库应用程序本地文件夹，或通过安装到本机程序集缓存 (WinSxS); 仍可以再分发但是，为已部署的应用程序可以通过使用简化的 Visual c + + 库维护[发布服务器配置文件](/windows/desktop/SbsCs/publisher-configuration)。 借助于独立应用程序部署模型，更加容易确保在特定计算机上运行的 C/C++ 应用程序使用 Visual C++ 库的最新版本，同时使系统管理员和应用程序的作者仍可以控制应用程序与其依赖 DLL 的显式版本绑定。

本节讨论如何将 C/C++ 应用程序生成为独立应用程序并确保使用清单将它绑定到 Visual C++ 库。 本部分中的信息主要适用于本机或非托管的 Visual C++ 应用程序。 有关部署使用 Visual C++ 生成的本机应用程序的信息，请参阅 [Redistributing Visual C++ Files](../ide/redistributing-visual-cpp-files.md)。

## <a name="in-this-section"></a>本节内容

[独立应用程序和并行程序集的概念](../build/concepts-of-isolated-applications-and-side-by-side-assemblies.md)

[生成 C/C++ 独立应用程序](../build/building-c-cpp-isolated-applications.md)

[生成 C/C++ 并行程序集](../build/building-c-cpp-side-by-side-assemblies.md)

[如何：生成免注册 COM 组件](../build/how-to-build-registration-free-com-components.md)

[如何：生成独立应用程序以使用 COM 组件](../build/how-to-build-isolated-applications-to-consume-com-components.md)

[了解 C/C++ 程序的清单生成](../build/understanding-manifest-generation-for-c-cpp-programs.md)

[C/C++ 独立应用程序和并行程序集疑难解答](../build/troubleshooting-c-cpp-isolated-applications-and-side-by-side-assemblies.md)

## <a name="related-sections"></a>相关章节

[独立应用程序和通过并行程序集](/windows/desktop/SbsCs/isolated-applications-and-side-by-side-assemblies-portal)

[部署桌面应用程序](../ide/deploying-native-desktop-applications-visual-cpp.md)