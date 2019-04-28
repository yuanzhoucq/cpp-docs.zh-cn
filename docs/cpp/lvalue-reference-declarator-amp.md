---
title: 左值引用声明符： &amp;
ms.date: 11/04/2016
f1_keywords:
- '&'
helpviewer_keywords:
- reference operator
- '& operator [C++], reference operator'
ms.assetid: edf0513d-3dcc-4663-b276-1269795dda51
ms.openlocfilehash: 7710b6f1efc2de770b26ad50923bde2ee5200f61
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62209549"
---
# <a name="lvalue-reference-declarator-amp"></a>左值引用声明符： &amp;

保留对象的地址，但行为方式在语法上与对象相似。

## <a name="syntax"></a>语法

```
type-id & cast-expression
```

## <a name="remarks"></a>备注

您可以将左值引用视为对象的另一名称。 左值引用声明由说明符的可选列表后跟一个引用声明符组成。 引用必须初始化且无法更改。

地址可转换为给定指针类型的任何对象也可转换为相似的引用类型。 例如，地址可转换为类型 `char *` 的任何对象也可转换为类型 `char &`。

请不要将引用声明与使用混淆[address-of 运算符](../cpp/address-of-operator-amp.md)。 当`&`*标识符*前面都有一个类型，如**int**或**char**，*标识符*声明为对的引用类型。 当`&`*标识符*前面没有类型，用法就是 address-of 运算符的。

## <a name="example"></a>示例

以下示例通过声明 `Person` 对象和对该对象的引用演示了引用声明符。 由于 `rFriend` 是对 `myFriend` 的引用，因此更新任一变量都将更改同一对象。

```cpp
// reference_declarator.cpp
// compile with: /EHsc
// Demonstrates the reference declarator.
#include <iostream>
using namespace std;

struct Person
{
    char* Name;
    short Age;
};

int main()
{
   // Declare a Person object.
   Person myFriend;

   // Declare a reference to the Person object.
   Person& rFriend = myFriend;

   // Set the fields of the Person object.
   // Updating either variable changes the same object.
   myFriend.Name = "Bill";
   rFriend.Age = 40;

   // Print the fields of the Person object to the console.
   cout << rFriend.Name << " is " << myFriend.Age << endl;
}
```

```Output
Bill is 40
```

## <a name="see-also"></a>请参阅

[参考资料](../cpp/references-cpp.md)<br/>
[引用类型函数自变量](../cpp/reference-type-function-arguments.md)<br/>
[引用类型函数返回](../cpp/reference-type-function-returns.md)<br/>
[对指针的引用](../cpp/references-to-pointers.md)