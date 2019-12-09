---
title: 编译器警告 C4577
description: 编译器警告 C4577 说明和解决方案。
ms.date: 09/18/2019
f1_keywords:
- C4577
helpviewer_keywords:
- C4577
ms.openlocfilehash: e29e47b2a268d86f7f6a280b79a1604fe6eff8a4
ms.sourcegitcommit: 8762a3f9b5476b4dee03f0ee8064ea606550986e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/04/2019
ms.locfileid: "74810557"
---
# <a name="compiler-warning-level-1-c4577"></a>编译器警告（等级1） C4577

> 在未指定异常处理模式的情况下使用 "noexcept";不保证异常终止。 指定/EHsc

编译器检测到 `noexcept` 规范，但未指定C++标准异常处理。 除非指定了[/ehsc](../../build/reference/eh-exception-handling-model.md)编译器选项，否则编译器不C++会完全支持基于标准的异常处理。 若要解决此问题，请设置 **/ehsc**编译器选项。

此警告是 Visual Studio 2015 中的新增功能，默认情况下处于关闭状态。 有关详细信息，请参阅[默认情况下处于关闭状态的编译器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。
