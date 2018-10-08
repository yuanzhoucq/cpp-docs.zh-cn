---
title: C 运行时错误 R6033 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6033
dev_langs:
- C++
helpviewer_keywords:
- R6033
ms.assetid: f9cffdc9-81bd-4a64-a698-02762cbd82c9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 64ff3069064b981ca1f4dd7b5c2d9a792cac8f26
ms.sourcegitcommit: 997e6b7d336cddb388bb6e9e56527725fcaa0624
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/08/2018
ms.locfileid: "48861857"
---
# <a name="c-runtime-error-r6033"></a>C 运行时错误 R6033

尝试使用此程序集在本机代码初始化过程中的 MSIL 代码。 这表示你的应用程序中的 bug。 它很可能是调用 MSIL 编译的结果 (/ clr) 从本机构造函数或从 DllMain 函数。

> [!NOTE]
> 如果运行应用时遇到此错误消息，该应用已关闭，因为它具有内部问题。 通过在应用中，bug 或外接程序或它使用的扩展中的 bug，可以导致此错误。
>
> 可以尝试以下步骤来修复此错误：
>
> - 使用**应用程序和功能**或**程序和功能**页**控制面板**来修复或重新安装该程序。
> - 使用**应用程序和功能**或**程序和功能**页**控制面板**删除、 修复或重新安装任何扩展插件或外接程序。
> - 检查**Windows Update**中**控制面板**的软件更新。
> - 检查应用程序的更新版本。 如果问题仍然存在，请与应用供应商联系。

**程序员提供的的信息**

此诊断指示在加载程序锁期间执行了 MSIL 指令。 如果已使用 /clr 标志编译本机 c + +，这可能发生。 只能对包含托管的代码的模块使用 /clr 标志。 有关详细信息，请参阅[混合程序集初始化](../../dotnet/initialization-of-mixed-assemblies.md)。