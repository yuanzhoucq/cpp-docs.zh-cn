---
title: const_cast 运算符
ms.date: 11/04/2016
f1_keywords:
- const_cast_cpp
helpviewer_keywords:
- const_cast keyword [C++]
ms.assetid: 4d8bb203-ef33-4a10-9f9f-c64d4fbc1687
ms.openlocfilehash: 36de296d1e871ca759108497922973ddea8e3382
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227551"
---
# <a name="const_cast-operator"></a>const_cast 运算符

**`const`** **`volatile`** **`__unaligned`** 从类中移除、和特性。

## <a name="syntax"></a>语法

```
const_cast <type-id> (expression)
```

## <a name="remarks"></a>备注

指向任何对象类型的指针或指向数据成员的指针可以显式转换为完全相同的类型 **`const`** （、 **`volatile`** 和限定符除外） **`__unaligned`** 。 对于指针和引用，结果将引用原始对象。 对于指向数据成员的指针，结果将引用与指向数据成员的原始（未强制转换）的指针相同的成员。 根据引用对象的类型，通过生成的指针、引用或指向数据成员的指针的写入操作可能产生未定义的行为。

不能使用 **`const_cast`** 运算符直接重写常量变量的常量状态。

**`const_cast`** 运算符将 null 指针值转换为目标类型的 null 指针值。

## <a name="example"></a>示例

```cpp
// expre_const_cast_Operator.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;
class CCTest {
public:
   void setNumber( int );
   void printNumber() const;
private:
   int number;
};

void CCTest::setNumber( int num ) { number = num; }

void CCTest::printNumber() const {
   cout << "\nBefore: " << number;
   const_cast< CCTest * >( this )->number--;
   cout << "\nAfter: " << number;
}

int main() {
   CCTest X;
   X.setNumber( 8 );
   X.printNumber();
}
```

在包含的行上 **`const_cast`** ，指针的数据类型 **`this`** 为 `const CCTest *` 。 **`const_cast`** 运算符将指针的数据类型更改 **`this`** 为 `CCTest *` ，从而允许修改该成员 `number` 。 强制转换仅对其所在的语句中的其余部分持续。

## <a name="see-also"></a>另请参阅

[转换运算符](../cpp/casting-operators.md)<br/>
[关键字](../cpp/keywords-cpp.md)
