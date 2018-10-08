---
title: C 运行时错误 R6028 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6028
dev_langs:
- C++
helpviewer_keywords:
- R6028
ms.assetid: 81e99079-4388-4244-a4f7-4641c508871c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dbcc1f34fced7a7ea752d8733662f7510a01aad5
ms.sourcegitcommit: 997e6b7d336cddb388bb6e9e56527725fcaa0624
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/08/2018
ms.locfileid: "48860545"
---
# <a name="c-runtime-error-r6028"></a>C 运行时错误 R6028

无法初始化堆

> [!NOTE]
> 如果运行应用时遇到此错误消息，该应用已关闭，因为它具有内部内存问题。 有多原因可能导致此错误，但通常导致非常低内存条件，该程序中的 bug 或有故障的硬件驱动程序。
>
> 可以尝试以下步骤来修复此错误：
>
> - 关闭其他正在运行的应用程序或重新启动计算机以释放内存。
> - 使用**应用程序和功能**或**程序和功能**页**控制面板**来修复或重新安装该程序。
> - 如果应用已使用另一个应用程序或驱动程序的最近安装之前，使用**应用程序和功能**或**程序和功能**页**控制面板**删除新的应用程序或驱动程序，然后重试您的应用程序。
> - 检查硬件供应商的网站或**Windows Update**中**控制面板**软件和驱动程序更新。
> - 检查应用程序的更新版本。 如果问题仍然存在，请与应用供应商联系。

**程序员提供的的信息**

当操作系统未能为应用程序创建内存池时，将发生此错误。 具体来说，C 运行时 (CRT) 调用的 Win32 函数 `HeapCreate` 返回了指示失败的 NULL。

如果在应用程序启动期间发生此错误，则系统可能会因为加载了有缺陷的驱动程序而无法满足堆请求。 请在 Windows Update 或硬件供应商的网站中查看已更新的驱动程序。