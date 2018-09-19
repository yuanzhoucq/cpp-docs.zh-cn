---
title: const_cast 运算符 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- const_cast_cpp
dev_langs:
- C++
helpviewer_keywords:
- const_cast keyword [C++]
ms.assetid: 4d8bb203-ef33-4a10-9f9f-c64d4fbc1687
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 314e8363fafa4f2a6649055f2c608cd5b7edd18c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46070068"
---
# <a name="constcast-operator"></a>const_cast 运算符

移除**const**，**易失性**，并 **__unaligned**个属性的类。

## <a name="syntax"></a>语法

```
const_cast <type-id> (expression)
```

## <a name="remarks"></a>备注

指向任何对象类型的指针或指向数据成员的指针可以显式转换为除完全相同的类型**const**，**易失性**，并 **__unaligned**限定符。 对于指针和引用，结果将引用原始对象。 对于指向数据成员的指针，结果将引用与指向数据成员的原始（未强制转换）的指针相同的成员。 根据引用对象的类型，通过生成的指针、引用或指向数据成员的指针的写入操作可能产生未定义的行为。

不能使用**const_cast**运算符直接重写常量变量的常量状态。

**Const_cast**运算符将 null 指针值转换为目标类型的 null 指针值。

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

在包含的行**const_cast**的数据类型**这**指针位于`const CCTest *`。 **Const_cast**运算符可更改的数据类型**这**指针，指向`CCTest *`，从而允许成员`number`要修改。 强制转换仅对其所在的语句中的其余部分持续。

## <a name="see-also"></a>请参阅

[强制转换运算符](../cpp/casting-operators.md)<br/>
[关键字](../cpp/keywords-cpp.md)