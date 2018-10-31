---
title: 编译器错误 C3728
ms.date: 11/04/2016
f1_keywords:
- C3728
helpviewer_keywords:
- C3728
ms.assetid: 6b510cb1-887f-4fcd-9a1f-3bb720417ed1
ms.openlocfilehash: 68aa23843b0470f15f409b6f3b58624f979ccfae
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50454582"
---
# <a name="compiler-error-c3728"></a>编译器错误 C3728

event： 事件没有引发方法

使用的语言创建的元数据，如 C# 中，不允许在其中定义的该类的外部引发的事件，是随[#using](../../preprocessor/hash-using-directive-cpp.md)指令和使用尝试的 CLR 编程的 Visual c + + 程序引发事件。

若要将提升在 C# 等语言中开发的程序中的事件，包含该事件的类需要还定义一个引发事件的公共方法。