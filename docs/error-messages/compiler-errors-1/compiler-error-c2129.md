---
title: 编译器错误 C2129
ms.date: 11/04/2016
f1_keywords:
- C2129
helpviewer_keywords:
- C2129
ms.assetid: 21a8223e-1d22-4baa-9ca1-922b7f751dd0
ms.openlocfilehash: 9cf414200dcfad8ae617e16e111bd26b19a315a6
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220426"
---
# <a name="compiler-error-c2129"></a>编译器错误 C2129

已声明但未定义静态函数 "function"

向从未定义的函数发出前向引用 **`static`** 。

**`static`** 必须在文件范围内定义函数。 如果该函数是在另一个文件中定义的，则必须将其声明为 **`extern`** 。
