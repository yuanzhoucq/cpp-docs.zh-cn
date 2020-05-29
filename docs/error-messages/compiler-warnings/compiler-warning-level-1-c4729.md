---
title: 编译器警告（等级 1）C4729
ms.date: 11/04/2016
f1_keywords:
- C4729
helpviewer_keywords:
- C4729
ms.assetid: 36a0151f-f258-48d9-9444-ae6d41ff70a4
ms.openlocfilehash: e78606f117251fa8ab1f08f2cef280a266309c32
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80185823"
---
# <a name="compiler-warning-level-1-c4729"></a>编译器警告（等级 1）C4729

根据警告，函数对于流图形太大

当函数太大，不能用可靠的方法（如检查是否有将生成警告的情况）进行编译时生成此警告。 仅在使用 [/Od](../../build/reference/od-disable-debug.md) 编译器选项时生成此警告。

若要解决此警告，请将函数拆成较小的函数。
