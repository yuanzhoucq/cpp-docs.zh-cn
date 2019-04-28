---
title: 编译器错误 C3744
ms.date: 11/04/2016
f1_keywords:
- C3744
helpviewer_keywords:
- C3744
ms.assetid: a447d050-80d1-406a-9a6e-f15c527d717c
ms.openlocfilehash: 407ed4b30b55b63aa9bf36de9f8675a531d70534
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62227097"
---
# <a name="compiler-error-c3744"></a>编译器错误 C3744

__unhook 必须有至少 3 个参数，针对托管事件

[__Unhook](../../cpp/unhook.md)函数必须采用三个参数时为托管扩展为编译的程序中使用C++。

`__hook` 和`__unhook`与 /clr 编程不兼容。 改为使用 + = 和-= 运算符。

C3744 才可访问使用已过时的编译器选项 **/clr: oldsyntax**。
