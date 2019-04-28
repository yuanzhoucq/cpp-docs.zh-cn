---
title: C 运行时错误 R6009
ms.date: 11/04/2016
f1_keywords:
- R6009
helpviewer_keywords:
- R6009
ms.assetid: edfb1f8b-3807-48f4-a994-318923b747ae
ms.openlocfilehash: 5e1914d5d2f665609cfc24c2db3dc8a123d7e83f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62299746"
---
# <a name="c-runtime-error-r6009"></a>C 运行时错误 R6009

没有足够的空间的环境

> [!NOTE]
> 如果运行应用时遇到此错误消息，该应用已关闭，因为它具有内部内存问题。 有多种原因引起此错误，但通常引起的极低内存条件，环境变量或该程序中的 bug 占用太多内存。
>
> 可以尝试以下步骤来修复此错误：
>
> - 关闭其他正在运行的应用程序或重新启动计算机以释放内存。
> - 使用**应用程序和功能**或**程序和功能**页**控制面板**来修复或重新安装该程序。
> - 检查**Windows Update**中**控制面板**的软件更新。
> - 检查应用程序的更新版本。 如果问题仍然存在，请与应用供应商联系。

**程序员提供的的信息**

出现内存不足，无法加载程序，但没有足够内存来创建**envp**数组。  这可能导致通过极低内存条件或非常大的环境变量的使用情况。 请考虑以下解决方案之一：

- 增加可用程序内存量。

- 减少的数量和大小的命令行参数。

- 通过删除不需要的变量来减少环境大小。