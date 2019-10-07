---
title: 部署本机桌面应用程序 (Visual C++)
ms.date: 05/11/2018
helpviewer_keywords:
- deploying applications [C++]
- application deployment [C++]
- Visual C++, application deployment
- application deployment [C++], about application deployment
- deploying applications [C++], about deploying applications
- distributing applications [C++]
ms.assetid: 37f1691e-d67c-41e4-926e-528a237a9bac
ms.topic: overview
ms.openlocfilehash: af3141a8fd626a909de93b219bf3b6d8186f0623
ms.sourcegitcommit: 7750e4c291d56221c8893120c56a1fe6c9af60d6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274749"
---
# <a name="deploying-native-desktop-applications-visual-c"></a>部署本机桌面应用程序 (Visual C++)

部署是用于分配要安装到其他计算机上的已完成应用程序或组件的进程。 当在开发人员计算机上创建了应用程序时开始部署规划。 当已安装并准备好在用户计算机上运行应用程序时，部署结束。

Visual Studio 提供用于部署 Windows 应用程序的不同技术。 其中包括 ClickOnce 部署和 Windows Installer 部署。

- ClickOnce 可用于部署面向公共语言运行时 (CLR) 的 C++ 应用程序 - 可以是混合程序集、纯程序集和可验证的程序集。 尽管可以使用 Windows Installer 部署托管的应用程序，但仍建议使用 ClickOnce，因为它利用 .NET Framework 安全功能（如清单签名）。 ClickOnce 不支持本机 C++ 应用程序的部署。 有关详细信息，请参阅[Visual c + + 应用程序的 ClickOnce 部署](clickonce-deployment-for-visual-cpp-applications.md)。

- Windows Installer 技术可以用于部署本机 C++ 应用程序或面向 CLR 的 C++ 应用程序。

文档本部分中的文章讨论如何确保本机 Visual C++ 应用程序可在任何提供受支持的目标平台的计算机上运行，安装包内必须包括哪些文件以及重新分发应用程序所依赖的组件的建议方式。

## <a name="in-this-section"></a>本节内容

- [Visual C++ 中的部署](deployment-in-visual-cpp.md)

- [部署概念](deployment-concepts.md)

- [了解 Visual C++ 应用程序的依赖项](understanding-the-dependencies-of-a-visual-cpp-application.md)

- [确定要重新分发的 DLL](determining-which-dlls-to-redistribute.md)

- [选择部署方法](choosing-a-deployment-method.md)

- [通用 CRT 部署](universal-crt-deployment.md)。

- [重新分发 Visual C++ 文件](redistributing-visual-cpp-files.md)

- [部署示例](deployment-examples.md)

- [重新分发 Web 客户端应用程序](redistributing-web-client-applications.md)

- [Visual C++ 应用程序的 ClickOnce 部署](clickonce-deployment-for-visual-cpp-applications.md)

- [在以前版本的运行时上运行 C++ /clr 应用程序](running-a-cpp-clr-application-on-a-previous-runtime-version.md)

## <a name="related-sections"></a>相关章节

- [生成 C/C++ 独立应用程序和并行程序集](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)

- [部署](/dotnet/framework/deployment/index)

- [C/C++ 独立应用程序和并行程序集疑难解答](../build/troubleshooting-c-cpp-isolated-applications-and-side-by-side-assemblies.md)