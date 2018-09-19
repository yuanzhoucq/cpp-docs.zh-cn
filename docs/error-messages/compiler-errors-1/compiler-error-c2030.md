---
title: 编译器错误 C2030 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2030
dev_langs:
- C++
helpviewer_keywords:
- C2030
ms.assetid: 5806cead-64df-4eff-92de-52c9a3f5ee62
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b0c5849c372cc4c7ebf27dbe010e65d406ad1ab1
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46032884"
---
# <a name="compiler-error-c2030"></a>编译器错误 C2030

具有“protected private”可访问性的析构函数不能是声明为“sealed”的类的成员

声明为 `sealed` 的 Windows 运行时类不能具有受保护的私有析构函数。 已密封的类型上只允许使用公共虚拟和私有非虚拟析构函数。 有关详细信息，请参阅[Ref 类和结构](../../cppcx/ref-classes-and-structs-c-cx.md)。

若要修复此错误，请更改析构函数的可访问性。