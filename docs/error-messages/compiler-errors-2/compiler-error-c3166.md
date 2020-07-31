---
title: 编译器错误 C3166
ms.date: 11/04/2016
f1_keywords:
- C3166
helpviewer_keywords:
- C3166
ms.assetid: ec3e330d-c15d-4158-8268-09101486c566
ms.openlocfilehash: 1915d58f73ce8d16135951b359c3f0fd48aea3ac
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230865"
---
# <a name="compiler-error-c3166"></a>编译器错误 C3166

> "指针"：不能将指向内部 __gc 指针的指针声明为 "type" 的成员

编译器找到了无效的指针声明（指向 **`__nogc`** 指针的指针 **`__gc`** ）。

只能使用过时的编译器选项访问 C3166 **`/clr:oldSyntax`** 。
