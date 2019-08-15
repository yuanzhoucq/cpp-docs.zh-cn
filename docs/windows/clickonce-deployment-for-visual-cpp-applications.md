---
title: Visual C++ 应用程序的 ClickOnce 部署
ms.date: 11/04/2016
helpviewer_keywords:
- deploying applications [C++], ClickOnce
- application deployment [C++], ClickOnce
- ClickOnce deployment [C++], C++ applications
ms.assetid: 9988c546-0936-452c-932f-9c76daa42157
ms.openlocfilehash: 4408db9d129c03ee5df9b006b03c6586df02afb1
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69513767"
---
# <a name="clickonce-deployment-for-visual-c-applications"></a>Visual C++ 应用程序的 ClickOnce 部署

Visual Studio 提供了两种不同的方法来部署 Windows 应用程序：ClickOnce 部署或 [Windows Installer](/windows/win32/Msi/windows-installer-portal) 部署。

## <a name="clickonce-deployment-in-c"></a>C++ 中的 ClickOnce 部署

可视化C++开发环境不直接支持使用 ClickOnce 部署 Visual Studio C++项目, 但可以使用工具。

> [!NOTE]
>  Visual Studio 支持在 Visual C# 和 Visual Basic 开发环境中使用 ClickOnce。 如果你的 Visual C++ Studio 项目是视觉C#对象的依赖项, 则可以从 Visual C#开发环境使用 ClickOnce 部署来发布应用程序 (包括其依赖项)。

要使用 ClickOnce 部署 Visual C++ 应用程序，首先必须使用 [Mage.exe（清单生成和编辑工具）](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)或其图形用户界面版本生成 [ClickOnce 应用程序清单](/visualstudio/deployment/clickonce-application-manifest)和 [ClickOnce 部署清单](/visualstudio/deployment/clickonce-deployment-manifest)。相关信息请参阅 [MageUI.exe（图形客户端中的清单生成和编辑工具）](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)。

首先使用 Mage.exe 生成应用程序清单；其结果文件具有扩展名 .manifest。 然后使用 Mage.exe 生成部署清单；其结果文件具有扩展名 .application。 然后对清单签名。

应用程序清单必须指定目标处理器（x86、x64 或 ARM）。 若要了解这些选项，请参阅[部署 64 位应用程序的必备组件](/visualstudio/deployment/deploying-prerequisites-for-64-bit-applications)。

此外，应用程序和部署清单的名称必须不同于 C++ 应用程序的名称。 这样可避免由 Mage.exe 创建的应用程序清单与作为 C++ 应用程序一部分的外部清单之间发生冲突。

部署时需安装应用程序依赖的所有 Visual C++ 库。 要确定特定应用程序的依赖项，可以使用 depends.exe 或带有 /DEPENDENTS 选项的 DUMPBIN 实用工具。 有关依赖项的详细信息，请参阅[了解 Visual C++ 应用程序的依赖项](understanding-the-dependencies-of-a-visual-cpp-application.md)。 可能需要运行 VCRedist.exe；此实用工具在目标计算机上安装 Visual C++ 库。

可能还需要为应用程序生成引导程序（必备安装程序）用于部署必备组件；有关引导程序的更多信息，请参阅[创建引导程序包](/visualstudio/deployment/creating-bootstrapper-packages)。

有关此技术的更详细说明，请参阅 [ClickOnce 安全和部署](/visualstudio/deployment/clickonce-security-and-deployment)。 有关 ClickOnce 部署的详细示例，请参阅[演练：手动部署 ClickOnce 应用程序](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application)。

## <a name="see-also"></a>请参阅

[Mage.exe（清单生成和编辑工具）](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)<br>
[MageUI.exe（图形化客户端中的清单生成和编辑工具）](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)<br>
[Makecert.exe（证书创建工具）](/windows/win32/SecCrypto/makecert)<br>
[部署桌面应用程序](deploying-native-desktop-applications-visual-cpp.md)<br>
[部署应用程序、服务和组件](/visualstudio/deployment/deploying-applications-services-and-components)<br>
[ClickOnce 安全和部署](/visualstudio/deployment/clickonce-security-and-deployment)<br>
[创建引导程序包](/visualstudio/deployment/creating-bootstrapper-packages)<br>
[使用 C++/CLI (Visual C++) 进行 .NET 编程](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)<br>
[本机和 .NET 的互操作性](../dotnet/native-and-dotnet-interoperability.md)
