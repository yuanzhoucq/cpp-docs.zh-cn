---
title: C 运行时错误 R6018
ms.date: 11/04/2016
f1_keywords:
- R6018
helpviewer_keywords:
- R6018
ms.assetid: f6dd40d1-a119-4d8b-b39e-97350ea23349
ms.openlocfilehash: 83ad191fe1518e5e6bab0798840415ef392db71e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197283"
---
# <a name="c-runtime-error-r6018"></a>C 运行时错误 R6018

意外堆错误

> [!NOTE]
> 如果在运行应用程序时遇到此错误消息，则该应用程序已关闭，因为它有一个内部问题。 此错误有几个可能的原因，但通常是由于应用程序的代码中的缺陷导致的。
>
> 可以尝试以下步骤来修复此错误：
>
> - 使用**控制面板**中的 "**应用和功能**" 或 "**程序和功能**" 页来修复或重新安装该程序。
> - 检查 "**控制面板**" 中的 "软件更新" **Windows 更新**。
> - 检查应用的更新版本。 如果问题仍然存在，请与应用程序供应商联系。

**面向程序员的信息**

程序执行内存管理操作时遇到意外错误。

如果程序无意中更改了运行时堆数据，通常会发生此错误。 但是，它也可能是由运行时或操作系统代码中的内部错误引起的。

若要解决此问题，请检查代码中的堆损坏错误。 有关详细信息和示例，请参阅[CRT 调试堆详细信息](/visualstudio/debugger/crt-debug-heap-details)。 接下来，请检查是否正在使用适用于你的应用部署的最新可再发行组件。 有关信息，请参阅[ C++Visual 中的部署](../../windows/deployment-in-visual-cpp.md)。
