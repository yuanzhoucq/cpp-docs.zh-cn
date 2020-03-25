---
title: 编译器错误 C2129
ms.date: 11/04/2016
f1_keywords:
- C2129
helpviewer_keywords:
- C2129
ms.assetid: 21a8223e-1d22-4baa-9ca1-922b7f751dd0
ms.openlocfilehash: a3e2268bfc5597668e8689d093a0c2bb7f18e037
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80207280"
---
# <a name="compiler-error-c2129"></a>编译器错误 C2129

已声明但未定义静态函数 "function"

对从未定义的 `static` 函数进行了正向引用。

必须在文件范围内定义 `static` 函数。 如果函数是在另一个文件中定义的，则必须将其声明 `extern`。
