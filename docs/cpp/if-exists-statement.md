---
title: __if_exists 语句
ms.date: 11/04/2016
f1_keywords:
- __if_exists_cpp
helpviewer_keywords:
- identifiers, testing for existence
- symbols, testing for existence
- __if_exists keyword [C++]
ms.assetid: d3eb34b6-f3a9-4063-a286-b62a28c0c7fa
ms.openlocfilehash: ea136ac0312b78519fe2d8ea88ace4d8b0d69946
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178413"
---
# <a name="__if_exists-statement"></a>__if_exists 语句

**__If_exists**语句测试指定的标识符是否存在。 如果该标识符存在，则执行指定的语句块。

## <a name="syntax"></a>语法

```
__if_exists ( identifier ) {
statements
};
```

#### <a name="parameters"></a>parameters

|参数|说明|
|---------------|-----------------|
|*identifier*|要测试其存在性的标识符。|
|*前瞻性*|*标识符*存在时要执行的一个或多个语句。|

## <a name="remarks"></a>备注

> [!CAUTION]
>  若要获得最可靠的结果，请在以下约束下使用 **__if_exists**语句。

- 将 **__if_exists**语句仅应用于简单类型，而不是模板。

- 将 **__if_exists**语句应用于类的内部或外部的标识符。 不要将 **__if_exists**语句应用于局部变量。

- 仅在函数体中使用 **__if_exists**语句。 在函数体的外部， **__if_exists**语句只能测试完全定义的类型。

- 在测试重载函数时，不能测试特定形式的重载。

**__If_exists**语句的补集是[__if_not_exists](../cpp/if-not-exists-statement.md)语句。

## <a name="example"></a>示例

请注意，此示例使用了模板，不建议这样做。

```cpp
// the__if_exists_statement.cpp
// compile with: /EHsc
#include <iostream>

template<typename T>
class X : public T {
public:
   void Dump() {
      std::cout << "In X<T>::Dump()" << std::endl;

      __if_exists(T::Dump) {
         T::Dump();
      }

      __if_not_exists(T::Dump) {
         std::cout << "T::Dump does not exist" << std::endl;
      }
   }
};

class A {
public:
   void Dump() {
      std::cout << "In A::Dump()" << std::endl;
   }
};

class B {};

bool g_bFlag = true;

class C {
public:
   void f(int);
   void f(double);
};

int main() {
   X<A> x1;
   X<B> x2;

   x1.Dump();
   x2.Dump();

   __if_exists(::g_bFlag) {
      std::cout << "g_bFlag = " << g_bFlag << std::endl;
   }

   __if_exists(C::f) {
      std::cout << "C::f exists" << std::endl;
   }

   return 0;
}
```

## <a name="output"></a>输出

```Output
In X<T>::Dump()
In A::Dump()
In X<T>::Dump()
T::Dump does not exist
g_bFlag = 1
C::f exists
```

## <a name="see-also"></a>另请参阅

[选择语句](../cpp/selection-statements-cpp.md)<br/>
[关键字](../cpp/keywords-cpp.md)<br/>
[__if_not_exists 语句](../cpp/if-not-exists-statement.md)
