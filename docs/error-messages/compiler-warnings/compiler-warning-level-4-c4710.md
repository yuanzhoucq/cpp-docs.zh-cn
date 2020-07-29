---
title: 编译器警告（等级 4）C4710
ms.date: 11/04/2016
f1_keywords:
- C4710
helpviewer_keywords:
- C4710
ms.assetid: 76381ec7-3fc1-4bee-9a0a-c2c8307b92e2
ms.openlocfilehash: c30b98204f447f4d9d0ab8d687602a361d909363
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218060"
---
# <a name="compiler-warning-level-4-c4710"></a>编译器警告（等级 4）C4710

"function"：函数未内联

为内联展开选择了给定函数，但编译器未执行内联。

内联是按编译器的判断来执行的。 **`inline`** 关键字（如 **`register`** 关键字）用作编译器的提示。 编译器使用试探法来确定是否应内联特定函数以加快编译速度时的代码速度，或是否应内联特定函数以便在编译空间时使代码更小。 编译时，编译器将仅内联非常小的函数。

在某些情况下，编译器不会出于机械原因而内联特定函数。 请参阅[C4714](../../error-messages/compiler-warnings/compiler-warning-level-4-c4714.md) ，以获取编译器可能未内联函数的原因列表。

默认情况下，此警告处于关闭状态。 请参阅 [默认情况下处于关闭状态的编译器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 了解详细信息。
