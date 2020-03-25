---
title: C 运行时错误 R6032
ms.date: 11/04/2016
f1_keywords:
- R6032
helpviewer_keywords:
- R6032
ms.assetid: 52092a63-cc51-444a-bfc3-fad965a3558e
ms.openlocfilehash: b29b946d08cff903cf0ca398ba0d7589cb5d54ea
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197088"
---
# <a name="c-runtime-error-r6032"></a>C 运行时错误 R6032

没有足够的空间用于区域设置信息

> [!NOTE]
> 如果在运行应用程序时遇到此错误消息，则该应用程序已关闭，因为它具有内部内存问题。 此错误有几个可能的原因，但通常是由于内存不足或程序中的 bug 引起的。
>
> 可以尝试以下步骤来修复此错误：
>
> - 关闭其他正在运行的应用程序或重新启动计算机以释放内存。
> - 使用**控制面板**中的 "**应用和功能**" 或 "**程序和功能**" 页来修复或重新安装该程序。
> - 检查 "**控制面板**" 中的 "软件更新" **Windows 更新**。
> - 检查应用的更新版本。 如果问题仍然存在，请与应用程序供应商联系。

**面向程序员的信息**

运行时在每个线程上维护有关区域设置的信息，以便能够处理对与区域设置相关的函数的调用。 如果此信息的内存分配失败，则运行时无法继续，因为它的许多基本设施依赖于它。
