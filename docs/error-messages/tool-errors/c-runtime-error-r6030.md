---
title: C 运行时错误 R6030
ms.date: 11/04/2016
f1_keywords:
- R6030
helpviewer_keywords:
- R6030
ms.assetid: 0238a6c3-a033-4046-8adc-f8f99d961153
ms.openlocfilehash: 5d7160623d4e1eb83240c09e637c780fefc0d43d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197114"
---
# <a name="c-runtime-error-r6030"></a>C 运行时错误 R6030

CRT 未初始化

> [!NOTE]
> 如果在运行应用程序时遇到此错误消息，则该应用程序已关闭，因为它有一个内部问题。 此问题最常见的原因通常是某些安全软件程序或程序中的 bug 很少导致。
>
> 可以尝试以下步骤来修复此错误：
>
> - 您的安全软件可能会提供有关缓解此问题的特定说明。 有关详细信息，请查看安全软件供应商的网站。 或者，检查安全软件的更新版本，或尝试不同的安全软件。
> - 使用**控制面板**中的 "**应用和功能**" 或 "**程序和功能**" 页来修复或重新安装该程序。
> - 检查 "**控制面板**" 中的 "软件更新" **Windows 更新**。
> - 检查应用的更新版本。 如果问题仍然存在，请与应用程序供应商联系。

**面向程序员的信息**

如果使用的是 C 运行时（CRT），但未执行 CRT 启动代码，则会出现此错误。 如果链接器开关[/ENTRY](../../build/reference/entry-entry-point-symbol.md)用于替代控制台 exe 的默认起始地址（**通常为** **MainCRTStartup**）、 **WinMainCRTStartup**或**wWinMainCRTStartup**用于 Windows exe，则可能会收到此错误，或为 DLL **_DllMainCRTStartup** 。 除非在启动时调用上述函数之一，否则将不会初始化 C 运行时。 当链接到 C 运行时库并使用 normal **main**、 **wmain**、 **WinMain**或**DllMain**入口点时，通常会默认调用这些启动函数。

在其他程序使用代码注入技术捕获某些 DLL 库调用时也可能会出现此错误。 一些侵入安全程序使用此方法。 在 visual Studio 2015 C++之前的 visual Studio 版本中，可以使用静态链接的 CRT 库来解决该问题，但出于安全和应用程序更新的原因，不建议这样做。 更正此问题可能需要最终用户操作。
