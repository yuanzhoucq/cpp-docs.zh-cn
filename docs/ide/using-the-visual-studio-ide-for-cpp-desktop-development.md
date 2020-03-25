---
title: 使用 Visual Studio IDE 进行 C++ 桌面开发
ms.date: 04/25/2019
helpviewer_keywords:
- IDE [C++]
- Visual Studio IDE [C++]
ms.assetid: d985c230-8e81-49d6-92be-2db9cac8d023
ms.openlocfilehash: 2cf2844fd4247c3c69648823302a6ad56ff5fd45
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80171771"
---
# <a name="using-the-visual-studio-ide-for-c-desktop-development"></a>使用 Visual Studio IDE 进行 C++ 桌面开发

Visual Studio 集成开发环境 (IDE) 提供一组功能，帮助你管理大型和小型代码项目、写入和重构代码以及使用静态分析和功能强大的调试工具检测和更正错误。 这一系列的文章旨在介绍在管理项目，写入、测试和调试代码，并将代码部署到其他计算机的过程中所需的每个步骤。

## <a name="prerequisites"></a>必备条件

如果尚未安装 Visual Studio，现在即可安装。 有关下载链接和快速演练，请参阅[在 Visual Studio 中安装 C++ 支持](../build/vscpp-step-0-installation.md)。 有关如何常规安装 Visual Studio 的详细信息以及出现错误时的故障排除提示，请参阅[安装 Visual Studio](/visualstudio/install/install-visual-studio)。 安装 Visual Studio 时，请务必选择“使用 C++ 的桌面开发”工作负荷以包含 C++ 编译器、工具和库，因为不会默认安装它们。

这些演练假定已安装 Visual Studio 和 Windows 桌面开发所需的 C++ 组件。 我们假定你了解 C++ 语言的基础知识。 如果需要了解 C++，这里有许多可用的书籍和 Web 资源。 “标准 C++ 基础”网站的[快速入门](https://isocpp.org/get-started)是一个不错的开始。

如果尚未安装 Visual Studio，现在即可安装。 一般情况下，强烈建议使用 Visual Studio 2019，即使需要使用 Visual Studio 2017 或 Visual Studio 2015 编译器编译代码。 有关详细信息，请参阅 [使用 Visual Studio 中的本机多重目标生成旧项目](../porting/use-native-multi-targeting.md)。

**Visual Studio 2019 安装**

若要获取 Visual Studio 2019，可从 [Visual Studio 下载](https://www.visualstudio.com/downloads/)进行下载。 请确保在安装 Visual Studio 时包含 C++ 开发工具，因为这些工具不会默认安装。 有关如何安装 Visual Studio 的详细信息，请参阅[安装 Visual Studio](/visualstudio/install/install-visual-studio)。

**Visual Studio 2017 安装**

若要获取 Visual Studio 2017，可从[下载 Visual Studio 的旧版本](https://www.visualstudio.com/vs/older-downloads/)进行下载。 请确保在安装 Visual Studio 时包含 C++ 开发工具，因为这些工具不会默认安装。 有关如何安装 Visual Studio 的详细信息，请参阅[安装 Visual Studio](/visualstudio/install/install-visual-studio) 并将页面上的版本选择器设置为“Visual Studio 2017”。

**Visual Studio 2015 安装**

若要安装 Visual Studio 2015，请转到[下载较旧版本的 Visual Studio](https://www.visualstudio.com/vs/older-downloads/)。 运行安装程序并选择“自定义安装”，然后选择 C++ 组件。

Visual Studio 安装完毕后，即可继续进行。

## <a name="get-started"></a>入门

若要开始使用 Visual Studio IDE 生成 C++ 应用，请按顺序完成这些主题的演练。 每一篇演练都基于之前完成的主题：

- [演练：使用项目和解决方案 (C++)](walkthrough-working-with-projects-and-solutions-cpp.md)

- [演练：生成项目 (C++)](walkthrough-building-a-project-cpp.md)

- [演练：测试项目 (C++)](walkthrough-testing-a-project-cpp.md)

- [演练：调试项目 (C++)](walkthrough-debugging-a-project-cpp.md)

- [演练：部署程序 (C++)](walkthrough-deploying-your-program-cpp.md)

## <a name="next-steps"></a>后续步骤

完成这些演练后，便已准备好开始生成自己的项目。 有关 C++ 开发的更多资源和信息，请参阅 [Visual Studio 中的 Visual C++](../overview/visual-cpp-in-visual-studio.md)。

## <a name="see-also"></a>另请参阅

[Visual Studio 开发入门](/visualstudio/ide/get-started-developing-with-visual-studio)
