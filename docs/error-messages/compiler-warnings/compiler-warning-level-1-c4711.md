---
title: 编译器警告（等级 1）C4711
ms.date: 11/04/2016
f1_keywords:
- C4711
helpviewer_keywords:
- C4711
ms.assetid: 270506ab-fead-4328-b714-2978113be238
ms.openlocfilehash: 9e2adf3583012a670f936c2b86a9ddc393fe53c6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175332"
---
# <a name="compiler-warning-level-1-c4711"></a>编译器警告（等级 1）C4711

为内联展开选定了函数“function”

尽管未将其标记为内联，但编译器在给定函数上执行了内联。

如果指定[/Ob2](../../build/reference/ob-inline-function-expansion.md) ，则启用 C4711。

内联是按编译器的判断来执行的。 此警告为信息性。

默认情况下，此警告处于关闭状态。 若要启用警告，请使用[#pragma 警告](../../preprocessor/warning.md)。 请参阅 [默认情况下处于关闭状态的编译器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 了解详细信息。
