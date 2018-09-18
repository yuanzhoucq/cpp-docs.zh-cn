---
title: 编译器警告 （等级 1） C4190 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4190
dev_langs:
- C++
helpviewer_keywords:
- C4190
ms.assetid: a4d0ad93-a19a-4063-addd-36d605831567
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d398331c159c6fc639160dbe54d6ab5f969d3dbd
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46063731"
---
# <a name="compiler-warning-level-1-c4190"></a>编译器警告 （等级 1） C4190

identifier1 具有 C 链接指定，但它返回 UDT 与 C 不兼容的 identifier2

函数指针作为返回类型具有 UDT （用户定义类型，这是类、 结构、 枚举或联合） 和`extern`"C"链接。 这是合法如果：

- 从 c + + 进行对此函数的所有调用。

- C + + 中是函数的定义。

## <a name="example"></a>示例

```cpp
// C4190.cpp
// compile with: /W1 /LD
struct X
{
   int i;
   X ();
   virtual ~X ();
};

extern "C" X func ();   // C4190
```