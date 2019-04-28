---
title: C 运行时错误 R6031
ms.date: 11/04/2016
f1_keywords:
- R6031
helpviewer_keywords:
- R6031
ms.assetid: 805d4cd1-cb2f-43fe-87e6-e7bd5b7329c5
ms.openlocfilehash: 6ef3f5fa7d063fdc300e6ac28ca519992525851c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62242677"
---
# <a name="c-runtime-error-r6031"></a>C 运行时错误 R6031

尝试初始化 CRT 不止一次。 这表示你的应用程序中的 bug。

> [!NOTE]
> 如果运行应用时遇到此错误消息，该应用已关闭，因为它具有内部问题。 在应用中，或通过中的外接程序或应用程序使用的扩展的 bug，这可能被由于 bug。
>
> 可以尝试以下步骤来修复此错误：
>
> - 使用**应用程序和功能**或**程序和功能**页**控制面板**来修复或重新安装该程序。
> - 使用**应用程序和功能**或**程序和功能**页**控制面板**要删除，请修复或重新安装应用使用的任何外接程序或扩展程序。
> - 检查**Windows Update**中**控制面板**的软件更新。
> - 检查应用程序的更新版本。 如果问题仍然存在，请与应用供应商联系。

**程序员提供的的信息**

此诊断指示在加载程序锁期间执行了 MSIL 指令。 有关详细信息，请参阅[混合程序集初始化](../../dotnet/initialization-of-mixed-assemblies.md)。