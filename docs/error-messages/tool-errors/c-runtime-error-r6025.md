---
title: C 运行时错误 R6025
ms.date: 11/04/2016
f1_keywords:
- R6025
helpviewer_keywords:
- R6025
ms.assetid: afa06d98-9c36-445b-b3e7-b6409bc8e779
ms.openlocfilehash: 461bfb2aa46053ec56fff67de70038b1fcd97389
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50639556"
---
# <a name="c-runtime-error-r6025"></a>C 运行时错误 R6025

纯虚函数调用

> [!NOTE]
> 如果运行应用时遇到此错误消息，该应用已关闭，因为它具有内部问题。 此错误的最常见原因是应用程序中或已损坏的安装中的 bug。
>
> 可以尝试以下步骤来修复此错误：
>
> - 使用**应用程序和功能**或**程序和功能**页**控制面板**来修复或重新安装该程序。
> - 检查**Windows Update**中**控制面板**的软件更新。
> - 检查应用程序的更新版本。 如果问题仍然存在，请与应用供应商联系。

**程序员提供的的信息**

实例化没有对象，来处理纯虚函数调用。

通过在通过指针创建的强制转换为派生类的类型，但实际指向基类的抽象基类中调用虚拟函数导致此错误。 可能会发生此转换从**void** <strong>\*</strong>为指向一个类时**void** <strong>\*</strong>是在基类的构造过程中创建。

