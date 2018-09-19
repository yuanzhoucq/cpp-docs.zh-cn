---
title: 编译器错误 C2095 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2095
dev_langs:
- C++
helpviewer_keywords:
- C2095
ms.assetid: 44f8ada1-974f-4e81-a408-33ac6695aa53
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 42fa7432dce465257b8179ba8a52b2654e0e5507
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46032457"
---
# <a name="compiler-error-c2095"></a>编译器错误 C2095

function： 实参具有 void 类型： 参数 number

传递给函数的参数的类型为`void`，这不允许。 使用指向 void 的指针 ( `void *`) 相反。

`number`指示哪个参数为`void`。