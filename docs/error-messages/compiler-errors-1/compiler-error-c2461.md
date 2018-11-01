---
title: 编译器错误 C2461
ms.date: 11/04/2016
f1_keywords:
- C2461
helpviewer_keywords:
- C2461
ms.assetid: e64ba651-f441-4fdb-b5cb-4209bbbe4db4
ms.openlocfilehash: e8f82ed4ce8ad77a22961a42c8e9a256e6f647db
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50535130"
---
# <a name="compiler-error-c2461"></a>编译器错误 C2461

> '*类*： 构造函数语法缺少形参

类的构造函数不会指定任何形式的参数。 构造函数的声明必须指定形参列表。 列表可以为空。

若要解决此问题，请添加一对圆括号的声明后*类*:: **类*。

## <a name="example"></a>示例

下面的示例演示如何修复错误 C2461:

```cpp
// C2461.cpp
// compile with: /c
class C {
   C::C;     // C2461
   C::C();   // OK
};
```