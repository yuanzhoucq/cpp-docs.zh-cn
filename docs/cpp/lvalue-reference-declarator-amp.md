---
title: Lvalue 引用声明符： &amp;
ms.date: 11/04/2016
f1_keywords:
- '&'
helpviewer_keywords:
- reference operator
- '& operator [C++], reference operator'
ms.assetid: edf0513d-3dcc-4663-b276-1269795dda51
ms.openlocfilehash: 595f2b683d2abb4cdc8a328dc6e86338ab90f214
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178062"
---
# <a name="lvalue-reference-declarator-amp"></a>Lvalue 引用声明符： &amp;

保留对象的地址，但行为方式在语法上与对象相似。

## <a name="syntax"></a>语法

```
type-id & cast-expression
```

## <a name="remarks"></a>备注

您可以将左值引用视为对象的另一名称。 左值引用声明由说明符的可选列表后跟一个引用声明符组成。 引用必须初始化且无法更改。

地址可转换为给定指针类型的任何对象也可转换为相似的引用类型。 例如，地址可转换为类型 `char *` 的任何对象也可转换为类型 `char &`。

不要将引用声明与[地址运算符](../cpp/address-of-operator-amp.md)的使用混淆。 如果 `&`*标识符*前面有一个类型，如**int**或**char**，则*标识符*将声明为对该类型的引用。 当 `&`*标识符*前面没有类型时，使用的是地址为的运算符。

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

## <a name="see-also"></a>另请参阅

[参考](../cpp/references-cpp.md)<br/>
[引用类型函数自变量](../cpp/reference-type-function-arguments.md)<br/>
[引用类型函数返回](../cpp/reference-type-function-returns.md)<br/>
[对指针的引用](../cpp/references-to-pointers.md)
