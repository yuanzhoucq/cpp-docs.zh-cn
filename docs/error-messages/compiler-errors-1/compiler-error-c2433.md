---
title: 编译器错误 C2433
ms.date: 11/04/2016
f1_keywords:
- C2433
helpviewer_keywords:
- C2433
ms.assetid: 7079fedd-6059-4125-82ef-ebe275f1f9d1
ms.openlocfilehash: 8a98fcf7570605694569b7ae466ae0a3c7cf14bb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50512043"
---
# <a name="compiler-error-c2433"></a>编译器错误 C2433

identifier: modifier 不允许在数据声明

`friend`， `virtual`，和`inline`修饰符不能用于数据声明。

## <a name="example"></a>示例

下面的示例生成 C2433。

```
// C2433.cpp
class C{};

int main() {
   inline C c;   // C2433
}
```