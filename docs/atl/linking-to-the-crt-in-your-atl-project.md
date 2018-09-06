---
title: 将链接到 ATL 项目中的 CRT |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
f1_keywords:
- DllMainCRTStartup
- wWinMainCRTStartup
- WinMainCRTStartup
dev_langs:
- C++
helpviewer_keywords:
- CRT, linking with ATL
- WinMainCRTStartup method
- DllMainCRTStartup method
- wWinMainCRTStartup method
- ATL, C Run-Time library (CRT)
ms.assetid: 650957ae-362c-4ecf-8b03-5d49138e8b5b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7d5548089f66a26f633e5692f1fe2199a8109904
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2018
ms.locfileid: "43764573"
---
# <a name="linking-to-the-crt-in-your-atl-project"></a>将链接到 ATL 项目中的 CRT

[C 运行时库](../c-runtime-library/crt-library-features.md)(CRT) 提供许多有用的功能，可以使编程更容易在 ATL 开发过程。 所有 ATL 项目都链接到 CRT 库。 您可以看到链接中的方法的优缺点[优点和缺点的方法用于链接到 CRT](../atl/benefits-and-tradeoffs-of-the-method-used-to-link-to-the-crt.md)。

## <a name="effects-of-linking-to-the-crt-on-your-program-image"></a>链接到 CRT 在程序映像上的效果

如果以静态方式链接到 CRT，CRT 中的代码放置在可执行映像，并且不需要运行你的映像的系统上已存在 CRT DLL。 如果动态链接到 CRT，CRT DLL 中的代码引用放置在你的映像，而不是代码本身。 为了使你的映像以在给定系统上运行，CRT DLL 必须在该系统上存在。 甚至当动态链接到 CRT，您可能会发现某些代码可以以静态方式链接 (例如， `DllMainCRTStartup`)。

当链接你的映像时，显式或隐式指定操作系统将调用加载图像后的入口点。 对于 DLL 的默认入口点是`DllMainCRTStartup`。 对于 EXE，它是`WinMainCRTStartup`。 您可以重写默认使用 /ENTRY 链接器选项。 CRT 提供一个实现`DllMainCRTStartup`， `WinMainCRTStartup`，和`wWinMainCRTStartup`（Unicode 入口点为 EXE）。 这些 CRT 提供入口点对全局对象调用构造函数，并初始化其他某些 CRT 函数所使用的数据结构。 此启动代码将大约 25 K 添加到你的映像，如果以静态方式链接。 如果动态链接，大部分代码是在 DLL 中，因此图像大小保持很小。

有关详细信息，请参阅链接器主题[/ENTRY （入口点符号）](../build/reference/entry-entry-point-symbol.md)。

## <a name="optimization-options"></a>优化选项

使用链接器选项 /opt: nowin98 可以进一步减少默认 ATL 控件 10k，通过牺牲增加加载 Windows 98 系统上的时间。 链接选项的详细信息，请参阅[/OPT （优化）](../build/reference/opt-optimizations.md)。

## <a name="see-also"></a>请参阅

[使用 ATL 和 C 运行时代码进行编程](../atl/programming-with-atl-and-c-run-time-code.md)   
[DLL 和 Visual C++ 运行时库行为](../build/run-time-library-behavior.md)

