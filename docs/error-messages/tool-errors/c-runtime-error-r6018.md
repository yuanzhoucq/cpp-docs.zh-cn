---
title: C 运行时错误 R6018
ms.date: 11/04/2016
f1_keywords:
- R6018
helpviewer_keywords:
- R6018
ms.assetid: f6dd40d1-a119-4d8b-b39e-97350ea23349
ms.openlocfilehash: b36e2184e5be131645fb4dd58a361fdb9a31da63
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "58774967"
---
# <a name="c-runtime-error-r6018"></a>C 运行时错误 R6018

意外的堆错误

> [!NOTE]
> 如果运行应用时遇到此错误消息，该应用已关闭，因为它具有内部问题。 有多种原因引起此错误，但通常由应用程序的代码中的一个缺陷。
>
> 可以尝试以下步骤来修复此错误：
>
> - 使用**应用程序和功能**或**程序和功能**页**控制面板**来修复或重新安装该程序。
> - 检查**Windows Update**中**控制面板**的软件更新。
> - 检查应用程序的更新版本。 如果问题仍然存在，请与应用供应商联系。

**程序员提供的的信息**

程序执行内存管理操作时遇到意外的错误。

如果该程序会无意中改变了运行时堆数据，通常会出现此错误。 但是，它可以也会导致运行时或操作系统代码中出现内部错误。

若要解决此问题，请检查在代码中的堆损坏错误。 有关详细信息和示例，请参阅[CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)。 接下来，检查您的应用程序部署使用最新可再发行组件。 有关信息，请参阅[Visual c + + 中的部署](../../windows/deployment-in-visual-cpp.md)。