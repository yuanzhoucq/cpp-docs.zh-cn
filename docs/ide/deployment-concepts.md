---
title: 部署概念 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Windows Installer [C++]
- dependencies [C++], application deployment and
- application deployment [C++], about application deployment
- deploying applications [C++], about deploying applications
- libraries [C++], application deployment issues
ms.assetid: ebd7f246-ab54-40e8-87fa-dac02c0047b3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0960e94acdbe660474efbeeddd0f72fa4f0606f6
ms.sourcegitcommit: 19a108b4b30e93a9ad5394844c798490cb3e2945
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2018
ms.locfileid: "34257057"
---
# <a name="deployment-concepts"></a>部署概念

本节介绍部署 C++ 应用程序的主要注意事项。

## <a name="windows-installer-deployment-in-c"></a>C++ 中的 Windows Installer 部署

Visual C++ 项目通常使用传统的 Windows Installer 安装程序进行部署。 要准备 Windows Installer 部署，请将应用程序打包为 setup.exe 文件，并将其与安装程序包 (.msi) 一起分发。 用户然后便可运行 setup.exe 来安装应用程序。

通过将安装项目添加到解决方案中来打包应用程序；生成时，它将创建分发给用户的安装和安装程序包文件。 有关详细信息，请参阅[选择部署方法](../ide/choosing-a-deployment-method.md)。

## <a name="library-dependencies"></a>库依赖项

如果 C/C++ 应用程序使用 Visual C++ 库提供的功能进行生成，则会依赖于这些库在运行时的存在性。 为确保应用程序能够运行，必须将应用程序静态或动态链接到必需的 Visual C++ 库。 如果应用程序动态链接到 Visual C++ 库，则在应用程序运行时，该库必须存在才能进行加载。 另一方面，如果应用程序静态链接到 Visual C++ 库，则用户计算机上无需存在相应的 DLL。 但是，静态链接会产生一些负面影响，例如增加应用程序文件的大小，并可能更难以维护。 有关详细信息，请参阅[使用 Dll 的优点](../build/dlls-in-visual-cpp.md#advantages-of-using-dlls)。

## <a name="packaging-and-redistributing"></a>打包和重新分发

Visual C++ 库打包为 DLL，所有用于 C/C++ 应用程序的必要库都由 Visual Studio 安装在开发者的计算机上。 但是，在向用户部署应用程序时，大多数情况下，要求用户安装 Visual Studio 才能运行应用程序是不可行的。 要能够重新分发应用程序正确运行所需的 Visual C++ 部件，这点很重要。

有关打包和重新分发的详细信息，请参阅以下主题：

- [确定要重新分发的 DLL](../ide/determining-which-dlls-to-redistribute.md)。

- [选择部署方法](../ide/choosing-a-deployment-method.md)。

- [通用 CRT 部署](universal-crt-deployment.md)。

有关疑难解答的部署示例和建议，请参阅：

- [部署示例](../ide/deployment-examples.md)。

- [C/C++ 独立应用程序和并行程序集疑难解答](../build/troubleshooting-c-cpp-isolated-applications-and-side-by-side-assemblies.md)。

## <a name="see-also"></a>请参阅

- [部署桌面应用程序](../ide/deploying-native-desktop-applications-visual-cpp.md)
- [了解 Visual C++ 应用程序的依赖项](../ide/understanding-the-dependencies-of-a-visual-cpp-application.md)
- [Windows Installer 部署](http://msdn.microsoft.com/en-us/121be21b-b916-43e2-8f10-8b080516d2a0)
