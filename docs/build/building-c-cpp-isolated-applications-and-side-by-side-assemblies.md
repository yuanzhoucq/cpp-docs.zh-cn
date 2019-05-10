---
title: 生成 C/C++ 独立应用程序和并行程序集
ms.date: 05/06/2019
helpviewer_keywords:
- isolated applications [C++]
- WinSxS [C++]
- native assembly cache [C++]
- builds [C++], isolated applications
- side-by-side applications [C++]
- builds [C++], side-by-side assemblies
ms.assetid: 9465904e-76f7-48bd-bb3f-c55d8f1699b6
ms.openlocfilehash: 8164ede1379e573b08f699cd55c199f6fa228823
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220970"
---
# <a name="building-cc-isolated-applications-and-side-by-side-assemblies"></a>生成 C/C++ 独立应用程序和并行程序集

Visual Studio 的理论基础是 Windows 客户端应用程序支持的部署模型[独立应用程序](/windows/desktop/SbsCs/isolated-applications)并[通过并行程序集](/windows/desktop/SbsCs/about-side-by-side-assemblies-)。 默认情况下，Visual Studio 将生成所有本机 C /C++使用的独立应用程序的应用程序[清单](/windows/desktop/sbscs/manifests)来描述在视觉对象上及其依赖项C++库。

将 C/C++ 程序生成为独立应用程序具有一系列的好处。 例如，当其他 C/C++ 应用程序安装或卸载 Visual C++ 库时，不会影响独立应用程序。 仍可将独立应用程序使用的 Visual C++ 库重新发布到应用程序的本地文件夹中或通过安装重新发布到本机程序集缓存 (WinSxS)；但是，通过使用 [发布者配置文件](/windows/desktop/SbsCs/publisher-configuration)，为已部署的应用程序提供 Visual C++ 库服务时会更加简单。 借助于独立应用程序部署模型，更加容易确保在特定计算机上运行的 C/C++ 应用程序使用 Visual C++ 库的最新版本，同时使系统管理员和应用程序的作者仍可以控制应用程序与其依赖 DLL 的显式版本绑定。

本节讨论如何将 C/C++ 应用程序生成为独立应用程序并确保使用清单将它绑定到 Visual C++ 库。 在本部分中的信息主要适用于本机或非托管，C++应用程序。 有关部署信息本机C++使用 Visual Studio 中，生成应用程序请参阅[重新分发 VisualC++文件](../windows/redistributing-visual-cpp-files.md)。

## <a name="in-this-section"></a>本节内容

[独立应用程序和并行程序集的概念](concepts-of-isolated-applications-and-side-by-side-assemblies.md)

[生成 C/C++ 独立应用程序](building-c-cpp-isolated-applications.md)

[生成 C/C++ 并行程序集](building-c-cpp-side-by-side-assemblies.md)

[如何：生成免注册的 COM 组件](how-to-build-registration-free-com-components.md)

[如何：生成独立应用程序以使用 COM 组件](how-to-build-isolated-applications-to-consume-com-components.md)

[了解 C/C++ 程序的清单生成](understanding-manifest-generation-for-c-cpp-programs.md)

[C/C++ 独立应用程序和并行程序集疑难解答](troubleshooting-c-cpp-isolated-applications-and-side-by-side-assemblies.md)

## <a name="related-sections"></a>相关章节

[独立应用程序和并行程序集](/windows/desktop/SbsCs/isolated-applications-and-side-by-side-assemblies-portal)

[部署桌面应用程序](../windows/deploying-native-desktop-applications-visual-cpp.md)