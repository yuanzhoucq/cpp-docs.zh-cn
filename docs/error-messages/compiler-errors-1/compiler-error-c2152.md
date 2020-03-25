---
title: 编译器错误 C2152
ms.date: 11/04/2016
f1_keywords:
- C2152
helpviewer_keywords:
- C2152
ms.assetid: a9ea2b0c-d55d-41c7-ba9f-dd75592ffc8a
ms.openlocfilehash: 10178d2cd40af60603b908a9351b8e14d12c5570
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80207189"
---
# <a name="compiler-error-c2152"></a>编译器错误 C2152

"identifier"：指向具有不同特性的函数的指针

指向函数的指针（`__cdecl`、`__stdcall`或 `__fastcall`）被分配给一个指针，该指针指向具有其他调用约定的函数。
