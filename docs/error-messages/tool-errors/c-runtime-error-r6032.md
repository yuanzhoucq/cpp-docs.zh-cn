---
title: C 运行时错误 R6032 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6032
dev_langs:
- C++
helpviewer_keywords:
- R6032
ms.assetid: 52092a63-cc51-444a-bfc3-fad965a3558e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 43155f24411fb5206a03d607f0551c2d34294aeb
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46024198"
---
# <a name="c-runtime-error-r6032"></a>C 运行时错误 R6032

没有足够的空间的区域设置信息

> [!NOTE]
>  如果运行应用时遇到此错误消息，该应用已关闭，因为它具有内部内存问题。 有多种原因引起此错误，但通常导致非常低内存的情况，或该程序中的 bug。
>
>  可以尝试以下步骤来修复此错误：
>
>  -   关闭其他正在运行的应用程序或重新启动计算机以释放内存。
> -   使用**应用程序和功能**或**程序和功能**页**控制面板**来修复或重新安装该程序。
> -   检查**Windows Update**中**控制面板**的软件更新。
> -   检查应用程序的更新版本。 如果问题仍然存在，请与应用供应商联系。

**程序员提供的的信息**

在运行时维护有关区域设置每个线程上的信息，以便它可以处理对区分区域设置的函数的调用。 如果此信息的内存分配失败，运行时无法继续，因为过多的基本功能依赖于它。