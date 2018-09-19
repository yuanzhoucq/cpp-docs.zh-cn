---
title: C 运行时错误 R6024 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6024
dev_langs:
- C++
helpviewer_keywords:
- R6024
ms.assetid: 0fb11c0f-9b81-4cab-81bd-4785742946a5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 10b258b12bb1ad7e47a7b126b8fd503814186645
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46041592"
---
# <a name="c-runtime-error-r6024"></a>C 运行时错误 R6024

_onexit/atexit 表没有足够的空间

> [!NOTE]
>  如果运行应用时遇到此错误消息，该应用已关闭，因为它具有内部内存问题。 此错误通常是通过极低内存条件或很少，该程序中的 bug 或它使用的 Visual c + + 库损坏引起的。
>
>  可以尝试以下步骤来修复此错误：
>
>  -   关闭其他正在运行的应用程序或重新启动计算机以释放内存。
> -   使用**应用程序和功能**或**程序和功能**页**控制面板**来修复或重新安装该程序。
> -   使用**应用程序和功能**或**程序和功能**页**控制面板**修复或重新安装的 Microsoft Visual c + + 可再发行的所有副本。
> -   检查**Windows Update**中**控制面板**的软件更新。
> -   检查应用程序的更新版本。 如果问题仍然存在，请与应用供应商联系。

**程序员提供的的信息**

出现此错误的原因时没有内存可供`_onexit`或`atexit`函数。 内存不足的情况被导致此错误。 你可以考虑在应用启动，以帮助在保存用户数据和执行干净的应用程序的预分配缓冲区内存不足情况中退出。