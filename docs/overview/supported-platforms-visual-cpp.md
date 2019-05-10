---
title: 支持的平台 (Visual C++)
ms.date: 11/04/2016
ms.technology: cpp-tools
helpviewer_keywords:
- Visual C++, platforms supported
- platforms [C++]
ms.assetid: 0d893056-4008-411a-b3d1-5f57fd7da95c
author: mikeblome
ms.author: mblome
ms.openlocfilehash: 39be17904f19bebdd9313a767de91a7315c3ca66
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "58782080"
---
# <a name="supported-platforms-visual-c"></a>支持的平台 (Visual C++)

使用 Visual Studio 生成的应用可以面向各种平台，如下所示。

|操作系统|x86|X64|ARM|
|----------------------|---------|---------|---------|
|Windows XP|X\*|X\*||
|Windows Server 2003|X\*|X\*||
|Windows Vista|X|X||
|Windows Server 2008|X|X||
|Windows 7|X|X||
|Windows Server 2012 R2|X|X||
|Windows 8|X|X|X|
|Windows 8.1|X|X|X|
|Windows 10|X|X|X|
|Android \*\*|X|X|X|
|iOS \*\*|X|X|X|
|Linux \*\*\*|X|X|X|

\*可以使用 Visual Studio 2017、Visual Studio 2015、Visual Studio 2013 和 Visual Studio 2012 Update 1 或更高版本中包括的 Windows XP 平台工具集生成 Windows XP 和 Windows Server 2003 项目。 有关如何使用此平台工具集的信息，请参阅[配置适用于 Windows XP 的程序](../build/configuring-programs-for-windows-xp.md)。 有关更改平台工具集的其他信息，请参阅 [如何：修改目标框架和平台工具集](../build/how-to-modify-the-target-framework-and-platform-toolset.md)。

\*\*可以安装 Visual Studio 2017 安装程序中的“使用 C++ 的移动开发”工作负荷（或者 Visual Studio 2015 安装中的“用于跨平台移动开发的 Visual C++”可选组件），面向 iOS 或 Android 平台。 有关说明，请参阅[安装用于跨平台移动开发的 Visual C++](/visualstudio/cross-platform/install-visual-cpp-for-cross-platform-mobile-development)。 要生成 iOS 代码，必须拥有 Mac 计算机并满足其他需求。 有关先决条件和安装说明的列表，请参阅[安装和配置工具以使用 iOS 进行生成](/visualstudio/cross-platform/install-and-configure-tools-to-build-using-ios)。 可以生成 x86 或 ARM 代码以匹配目标硬件。 使用 x86 配置以针对 iOS 模拟器、Microsoft Visual Studio Emulator for Android 和某些 Android 设备进行生成。 使用 ARM 配置以针对 iOS 设备和大多数 Android 设备进行生成。

\*\*\*可以安装 Visual Studio 2017 安装程序中的“使用 C++ 的 Linux 开发”工作负荷，面向 Linux 平台。 有关说明，请参阅[下载、安装和设置 Linux 工作负荷](../linux/download-install-and-setup-the-linux-development-workload.md)。 此工具集在目标计算机上编译可执行文件，使用户能够为支持的任何体系结构执行生成操作。

有关如何设置目标平台配置的信息，请参阅 [如何：针对 64 位 x64 平台配置 Visual C++ 项目](../build/how-to-configure-visual-cpp-projects-to-target-64-bit-platforms.md)。

## <a name="see-also"></a>请参阅

- [Visual Studio 版本中的 Visual C++ 工具和功能](visual-cpp-tools-and-features-in-visual-studio-editions.md)
- [入门](/visualstudio/ide/getting-started-with-cpp-in-visual-studio)
