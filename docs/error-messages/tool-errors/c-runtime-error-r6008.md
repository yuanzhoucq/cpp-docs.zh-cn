---
title: C 运行时错误 R6008 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6008
dev_langs:
- C++
helpviewer_keywords:
- R6008
ms.assetid: f0f304fc-709a-4843-bc7e-bad1ae0d1649
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 604b54d1c1752c76e28680e3373913ca7e92a9bc
ms.sourcegitcommit: 997e6b7d336cddb388bb6e9e56527725fcaa0624
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/08/2018
ms.locfileid: "48860428"
---
# <a name="c-runtime-error-r6008"></a>C 运行时错误 R6008

自变量没有足够的空间

> [!NOTE]
> 如果运行应用时遇到此错误消息，该应用已关闭，因为它具有内部内存问题。 有多种原因引起此错误，但通常引起的极低内存条件，环境变量或该程序中的 bug 占用太多内存。
>
> 可以尝试以下步骤来修复此错误：
>
> - 关闭其他正在运行的应用程序或重新启动计算机以释放内存。
> - 降低向应用程序的数量和大小的命令行参数。
> - 使用**应用程序和功能**或**程序和功能**页**控制面板**来修复或重新安装该程序。
> - 检查**Windows Update**中**控制面板**的软件更新。
> - 检查应用程序的更新版本。 如果问题仍然存在，请与应用供应商联系。

**程序员提供的的信息**

出现内存不足，无法加载程序，但没有足够内存来创建**argv**数组。 这可能导致通过极低内存条件或非常大的命令行或环境变量的使用情况。 请考虑以下解决方案之一：

- 增加可用程序内存量。

- 减少的数量和大小的命令行参数。

- 通过删除不需要的变量来减少环境大小。