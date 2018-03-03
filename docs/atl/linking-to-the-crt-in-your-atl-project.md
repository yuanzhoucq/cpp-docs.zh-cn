---
title: "将链接到 ATL 项目中的 CRT |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 631426fece3960303d67d8929e99c404beaab998
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="linking-to-the-crt-in-your-atl-project"></a>链接到 CRT 的内容在 ATL 项目
[C 运行时库](../c-runtime-library/crt-library-features.md)(CRT) 提供可以使编程更容易在 ATL 开发过程中的许多有用的功能。 所有 ATL 项目都链接到 CRT 库。 你可以看到的优点和缺点的链接中的方法[优点和缺点为链接到 CRT 方法使用](../atl/benefits-and-tradeoffs-of-the-method-used-to-link-to-the-crt.md)。  
  
## <a name="effects-of-linking-to-the-crt-on-your-program-image"></a>链接到 CRT 的内容在程序映像上的效果  
 如果你静态链接到 CRT 的内容，CRT 中的代码放置在可执行映像，并且不需要具有在系统运行你的映像上存在 CRT DLL。 如果动态链接到 CRT 的内容，对 CRT DLL 中的代码的引用都将置于你的映像，但不是代码本身。 为了使您的映像以给定的系统上运行，CRT DLL 必须在该系统上存在。 甚至当动态链接到 CRT 的内容，你可能会发现某些代码可以静态链接 (例如， **DllMainCRTStartup**)。  
  
 当链接你的映像时，你显式或隐式指定操作系统加载映像后将调入的入口点。 默认入口点是 dll， **DllMainCRTStartup**。 对于 EXE，它是**WinMainCRTStartup**。 你可以重写的默认方式 /ENTRY 链接器选项。 CRT 提供了有关实现**DllMainCRTStartup**， **WinMainCRTStartup**，和**wWinMainCRTStartup** （Unicode 入口点的 EXE）。 这些 CRT 提供入口点调用全局对象上的构造函数并初始化某些 CRT 函数使用其他数据结构。 此启动代码将大约 25 K 添加到你的映像，如果它以静态方式链接。 如果动态链接，大部分代码是在 DLL 中，因此图像的大小保持很小。  
  
 有关详细信息，请参阅链接器主题[/ENTRY （入口点符号）](../build/reference/entry-entry-point-symbol.md)。  
  
## <a name="optimization-options"></a>优化选项  
 使用链接器选项 /opt: nowin98 可以进一步减少 10k，通过默认 ATL 控件的 expense 在增加加载 Windows 98 系统上的时间。 链接选项的详细信息，请参阅[/OPT （优化）](../build/reference/opt-optimizations.md)。  
  
## <a name="see-also"></a>请参阅  
 [使用 ATL 和 C 运行时代码编程](../atl/programming-with-atl-and-c-run-time-code.md)   
 [DLL 和 Visual C++ 运行时库行为](../build/run-time-library-behavior.md)

