---
title: C 运行时错误 R6024
ms.date: 11/04/2016
f1_keywords:
- R6024
helpviewer_keywords:
- R6024
ms.assetid: 0fb11c0f-9b81-4cab-81bd-4785742946a5
ms.openlocfilehash: de89d2e9e2b34f40b906a5dacca4179eade23f7e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197192"
---
# <a name="c-runtime-error-r6024"></a>C 运行时错误 R6024

没有足够的空间用于 _onexit/atexit 表

> [!NOTE]
> 如果在运行应用程序时遇到此错误消息，则该应用程序已关闭，因为它具有内部内存问题。 此错误通常是由极少的内存情况引起的，或者很少是由程序中的 bug 或其使用的视觉C++对象损坏引起的。
>
> 可以尝试以下步骤来修复此错误：
>
> - 关闭其他正在运行的应用程序或重新启动计算机以释放内存。
> - 使用**控制面板**中的 "**应用和功能**" 或 "**程序和功能**" 页来修复或重新安装该程序。
> - 使用**控制面板**中的C++ "**应用和功能**" 或 "**程序和功能**" 页来修复或重新安装 Microsoft Visual 可再发行组件的所有副本。
> - 检查 "**控制面板**" 中的 "软件更新" **Windows 更新**。
> - 检查应用的更新版本。 如果问题仍然存在，请与应用程序供应商联系。

**面向程序员的信息**

发生此错误的原因是 `_onexit` 或 `atexit` 函数没有可用的内存。 此错误是由于内存不足造成的。 可以考虑在应用程序启动时预先分配缓冲区，以帮助保存用户数据，并在内存不足的情况下执行干净的应用退出。
