---
title: C 运行时错误 R6008
ms.date: 11/04/2016
f1_keywords:
- R6008
helpviewer_keywords:
- R6008
ms.assetid: f0f304fc-709a-4843-bc7e-bad1ae0d1649
ms.openlocfilehash: 214b6548cc7a3b880223503c2f3e9222d64212ca
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197388"
---
# <a name="c-runtime-error-r6008"></a>C 运行时错误 R6008

没有足够的空间用于参数

> [!NOTE]
> 如果在运行应用程序时遇到此错误消息，则该应用程序已关闭，因为它具有内部内存问题。 此错误有几个可能的原因，但通常是由于内存不足的情况、环境变量占用的内存过多，或者程序中存在 bug。
>
> 可以尝试以下步骤来修复此错误：
>
> - 关闭其他正在运行的应用程序或重新启动计算机以释放内存。
> - 减少应用程序的命令行参数的数量和大小。
> - 使用**控制面板**中的 "**应用和功能**" 或 "**程序和功能**" 页来修复或重新安装该程序。
> - 检查 "**控制面板**" 中的 "软件更新" **Windows 更新**。
> - 检查应用的更新版本。 如果问题仍然存在，请与应用程序供应商联系。

**面向程序员的信息**

有足够的内存来加载程序，但没有足够的内存来创建**argv**数组。 这可能是由于内存不足或异常的命令行或环境变量使用而导致的。 请考虑以下解决方案之一：

- 增加程序可用的内存量。

- 减少命令行参数的数量和大小。

- 通过删除不必要的变量来减少环境大小。
