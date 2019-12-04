---
title: 编译器错误 C3194
ms.date: 11/04/2016
f1_keywords:
- C3194
helpviewer_keywords:
- C3194
ms.assetid: 49d3ffc6-eff6-4b46-865b-18811692a8bb
ms.openlocfilehash: 83c07da5383740ca14c9b9de6224f47cf844d5fa
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757639"
---
# <a name="compiler-error-c3194"></a>编译器错误 C3194

"member"：值类型不能具有赋值运算符

需要编译器自动调用的特殊成员函数，例如复制构造函数或复制赋值运算符，在值类中不受支持。

## <a name="example"></a>示例

下面的示例生成 C3194。

```cpp
// C3194.cpp
// compile with: /clr /c
value struct MyStruct {
   MyStruct& operator= (const MyStruct& i) { return *this; }   // C3194
};

ref struct MyStruct2 {
   MyStruct2% operator= (const MyStruct2% i) { return *this; }   // OK
};
```
