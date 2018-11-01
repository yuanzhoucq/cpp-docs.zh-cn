---
title: 编译器警告 C4746
ms.date: 11/04/2016
ms.assetid: 5e79ab46-6031-499a-a986-716c866b6c0e
ms.openlocfilehash: 1b79eed2134b8c6310e508e56b3388c6f38fe4b7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50625883"
---
# <a name="compiler-warning-c4746"></a>编译器警告 C4746

可变访问\<表达式 > 受 /volatile: [iso&#124;ms] 设置; 请考虑使用 __iso_volatile_load/store 内部函数。

直接访问可变变量时会发出 C4746。 它旨在帮助开发人员识别受当前指定的特定可变模型的代码位置 (这可以使用控制[/volatile](../../build/reference/volatile-volatile-keyword-interpretation.md)编译器选项)。 具体而言，如果要在使用 /volatile:ms 时查找编译器生成的硬件内存屏障，它很有用。

__iso_volatile_load/store 内部函数可用于显式访问可变内存而不会受可变模型的影响。 使用这些内部函数不会触发 C4746。

默认情况下，此警告处于关闭状态。 请参阅 [默认情况下处于关闭状态的编译器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 了解详细信息。