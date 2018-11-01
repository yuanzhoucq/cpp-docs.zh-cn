---
title: 编译器错误 C2865
ms.date: 11/04/2016
f1_keywords:
- C2865
helpviewer_keywords:
- C2865
ms.assetid: 973eb6a0-c99a-4d25-b3e5-fe0539794d77
ms.openlocfilehash: e95714f7a10c1c25562e8b12025ede486e66cff8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50532718"
---
# <a name="compiler-error-c2865"></a>编译器错误 C2865

function： 非法 handle_or_pointer 比较

可以将对引用进行比较[类和结构](../../windows/classes-and-structs-cpp-component-extensions.md)或托管仅对是否相等的引用类型，以查看它们是否引用同一个对象 （= =） 或不同的对象 (！ =)。

无法比较它们的排序顺序，因为.NET 运行时可能会将托管的对象移动在任何时候，从而更改测试的结果。