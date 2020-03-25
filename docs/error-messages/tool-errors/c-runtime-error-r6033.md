---
title: C 运行时错误 R6033
ms.date: 11/04/2016
f1_keywords:
- R6033
helpviewer_keywords:
- R6033
ms.assetid: f9cffdc9-81bd-4a64-a698-02762cbd82c9
ms.openlocfilehash: 86ac98a2635975b811c7b50020e4d4782675ae4d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197012"
---
# <a name="c-runtime-error-r6033"></a>C 运行时错误 R6033

在本机代码初始化期间尝试使用此程序集中的 MSIL 代码。 这表示应用程序中有 bug。 这很可能是从本机构造函数或 DllMain 调用 MSIL 编译（/clr）函数的结果。

> [!NOTE]
> 如果在运行应用程序时遇到此错误消息，则该应用程序已关闭，因为它有一个内部问题。 此错误可能是由应用程序中的 bug 或其使用的外接程序或扩展中的 bug 引起的。
>
> 可以尝试以下步骤来修复此错误：
>
> - 使用**控制面板**中的 "**应用和功能**" 或 "**程序和功能**" 页来修复或重新安装该程序。
> - 使用**控制面板**中的 "**应用和功能**" 或 "**程序和功能**" 页，可以删除、修复或重新安装任何扩展或外接程序。
> - 检查 "**控制面板**" 中的 "软件更新" **Windows 更新**。
> - 检查应用的更新版本。 如果问题仍然存在，请与应用程序供应商联系。

**面向程序员的信息**

此诊断指示在加载程序锁定过程中正在执行 MSIL 指令。 如果已使用/clr 标志编译了本机C++ ，则会发生这种情况。 仅对包含托管代码的模块使用/clr 标志。 有关详细信息，请参阅[混合程序集的初始化](../../dotnet/initialization-of-mixed-assemblies.md)。
