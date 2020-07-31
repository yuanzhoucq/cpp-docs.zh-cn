---
title: 编译器警告 C4577
description: 编译器警告 C4577 说明和解决方案。
ms.date: 09/18/2019
f1_keywords:
- C4577
helpviewer_keywords:
- C4577
ms.openlocfilehash: fb9d412196e7764326a397a4bf6e76c8723ac2ae
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87196248"
---
# <a name="compiler-warning-level-1-c4577"></a>编译器警告（等级1） C4577

> 在未指定异常处理模式的情况下使用 "noexcept";不保证异常终止。 指定/EHsc

编译器检测到 **`noexcept`** 规范，但未指定标准 c + + 异常处理。 除非指定了[/ehsc](../../build/reference/eh-exception-handling-model.md)编译器选项，否则编译器不会完全支持根据 c + + 标准进行的异常处理。 若要解决此问题，请设置 **/ehsc**编译器选项。

此警告是 Visual Studio 2015 中的新增功能，默认情况下处于关闭状态。 有关详细信息，请参阅[默认情况下处于关闭状态的编译器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。
