---
title: 编译器错误 C3744
ms.date: 11/04/2016
f1_keywords:
- C3744
helpviewer_keywords:
- C3744
ms.assetid: a447d050-80d1-406a-9a6e-f15c527d717c
ms.openlocfilehash: 407ed4b30b55b63aa9bf36de9f8675a531d70534
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50516228"
---
# <a name="compiler-error-c3744"></a>编译器错误 C3744

__unhook 必须有至少 3 个参数，针对托管事件

[__Unhook](../../cpp/unhook.md)函数必须采用三个参数时在 c + + 托管扩展编译的程序中使用。

`__hook` 和`__unhook`与 /clr 编程不兼容。 改为使用 + = 和-= 运算符。

C3744 才可访问使用已过时的编译器选项 **/clr: oldsyntax**。
