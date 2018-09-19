---
title: 编译器错误 C2865 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2865
dev_langs:
- C++
helpviewer_keywords:
- C2865
ms.assetid: 973eb6a0-c99a-4d25-b3e5-fe0539794d77
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cc0a49f8e6ab42f7e607cd5f4f7cc91f6895abe0
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46035157"
---
# <a name="compiler-error-c2865"></a>编译器错误 C2865

function： 非法 handle_or_pointer 比较

可以将对引用进行比较[类和结构](../../windows/classes-and-structs-cpp-component-extensions.md)或托管仅对是否相等的引用类型，以查看它们是否引用同一个对象 （= =） 或不同的对象 (！ =)。

无法比较它们的排序顺序，因为.NET 运行时可能会将托管的对象移动在任何时候，从而更改测试的结果。