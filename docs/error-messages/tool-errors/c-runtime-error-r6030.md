---
title: C 运行时错误 R6030 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6030
dev_langs:
- C++
helpviewer_keywords:
- R6030
ms.assetid: 0238a6c3-a033-4046-8adc-f8f99d961153
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 63606624e1cbcc5ef2c5ea453ee6d346e3e686a8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46038121"
---
# <a name="c-runtime-error-r6030"></a>C 运行时错误 R6030

未初始化的 CRT

> [!NOTE]
>  如果运行应用时遇到此错误消息，该应用已关闭，因为它具有内部问题。 特定安全的软件程序，或很少，该程序中的 bug，通常被导致此问题。
>
>  可以尝试以下步骤来修复此错误：
>
>  -   安全软件可能的缓解此问题的具体说明。 检查安全软件供应商的网站了解详细信息。 或者，检查有更新版本的安全软件，或尝试使用不同的安全软件。
> -   使用**应用程序和功能**或**程序和功能**页**控制面板**来修复或重新安装该程序。
> -   检查**Windows Update**中**控制面板**的软件更新。
> -   检查应用程序的更新版本。 如果问题仍然存在，请与应用供应商联系。

**程序员提供的的信息**

如果你正在使用 C 运行时 (CRT)，但不是执行 CRT 启动代码，会发生此错误。 可能出现此错误，如果链接器开关[/ENTRY](../../build/reference/entry-entry-point-symbol.md)用于重写的默认开始地址，通常**mainCRTStartup**， **wmainCRTStartup**为控制台 exe 文件， **WinMainCRTStartup**或**wWinMainCRTStartup**为 Windows exe 文件，或 **_DllMainCRTStartup** dll。 除非在启动时调用上面的函数之一，C 运行时将不会初始化。 链接到 C 运行时库和使用普通时，默认情况下通常调用这些启动函数**主要**， **wmain**， **WinMain**，或**DllMain**入口点。

还有可能出现此错误，另一个程序使用代码注入技术来捕获某些 DLL 库调用时。 某些具有侵入性安全程序使用此方法。 在 Visual Studio 2015 之前的 Visual c + + 版本，则可以使用静态链接的 CRT 库为解决问题，但不是建议这样做的安全性和应用程序更新的原因。 更正此问题可能需要最终用户操作。