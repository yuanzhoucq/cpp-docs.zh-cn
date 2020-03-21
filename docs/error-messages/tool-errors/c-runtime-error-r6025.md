---
title: C 运行时错误 R6025
ms.date: 11/04/2016
f1_keywords:
- R6025
helpviewer_keywords:
- R6025
ms.assetid: afa06d98-9c36-445b-b3e7-b6409bc8e779
ms.openlocfilehash: d5edb08278b7b6b9b3eb62e92fc04410f96a8f09
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/21/2020
ms.locfileid: "80075132"
---
# <a name="c-runtime-error-r6025"></a>C 运行时错误 R6025

纯虚函数调用

> [!NOTE]
> 如果在运行应用程序时遇到此错误消息，则该应用程序已关闭，因为它有一个内部问题。 此错误的最常见原因是应用中的 bug 或安装已损坏。
>
> 可以尝试以下步骤来修复此错误：
>
> - 使用**控制面板**中的 "**应用和功能**" 或 "**程序和功能**" 页来修复或重新安装该程序。
> - 检查 "**控制面板**" 中的 "软件更新" **Windows 更新**。
> - 检查应用的更新版本。 如果问题仍然存在，请与应用程序供应商联系。

**面向程序员的信息**

尚未实例化对象来处理纯虚函数调用。

此错误是由通过转换为派生类的类型创建的指针调用抽象基类中的虚函数引起的，但实际上是指向基类的指针。 当从**void** <strong>\*</strong>强制转换为指向类的指针时，如果在构造基类的过程中创建了**void** <strong>\*</strong> ，则会发生这种情况。
