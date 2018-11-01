---
title: 编译器警告（等级 4）C4710
ms.date: 11/04/2016
f1_keywords:
- C4710
helpviewer_keywords:
- C4710
ms.assetid: 76381ec7-3fc1-4bee-9a0a-c2c8307b92e2
ms.openlocfilehash: 0f8e66982192f8af6498c9151d32a44226e0560a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50487771"
---
# <a name="compiler-warning-level-4-c4710"></a>编译器警告（等级 4）C4710

function： 函数未内联

为内联扩展选定了给定的函数，但编译器未执行内联。

在由编译器自行执行内联。 **内联**关键字，如**注册**关键字，用作编译器提示。 编译器使用试探法来确定是否应以加快速度，编译时代码特定函数进行内联，或应使代码更小，编译以下位置的空间时特定函数进行内联。 编译以下位置的空间时，编译器将唯一内联非常小的函数。

在某些情况下，编译器将不内联某个特定函数的机械的原因。 请参阅[C4714](../../error-messages/compiler-warnings/compiler-warning-level-4-c4714.md)有关编译器可能不内联函数的原因列表。

默认情况下，此警告处于关闭状态。 请参阅 [默认情况下处于关闭状态的编译器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 了解详细信息。