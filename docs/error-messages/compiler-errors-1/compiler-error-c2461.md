---
title: 编译器错误 C2461
ms.date: 11/04/2016
f1_keywords:
- C2461
helpviewer_keywords:
- C2461
ms.assetid: e64ba651-f441-4fdb-b5cb-4209bbbe4db4
ms.openlocfilehash: 3d290bd2288f76d0ddefa2057e3e01c9edc3cbc7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80205317"
---
# <a name="compiler-error-c2461"></a>编译器错误 C2461

> "*class*"：构造函数语法缺少形参

类的构造函数未指定任何形参。 构造函数的声明必须指定形参列表。 列表可以为空。

若要解决此问题，请在*class*：:**类*的声明后面添加一对括号。

## <a name="example"></a>示例

下面的示例演示如何修复 C2461：

```cpp
// C2461.cpp
// compile with: /c
class C {
   C::C;     // C2461
   C::C();   // OK
};
```
