---
title: 编译器错误 C2152
ms.date: 11/04/2016
f1_keywords:
- C2152
helpviewer_keywords:
- C2152
ms.assetid: a9ea2b0c-d55d-41c7-ba9f-dd75592ffc8a
ms.openlocfilehash: f2949aba53ba7a2e977405cf2e03c22f3aeac646
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87210028"
---
# <a name="compiler-error-c2152"></a>编译器错误 C2152

"identifier"：指向具有不同特性的函数的指针

指向带有一个调用约定的函数（、或）的指针被分配给一个指针，该指针指向 **`__cdecl`** **`__stdcall`** **`__fastcall`** 具有其他调用约定的函数。
