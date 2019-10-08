---
title: bad_cast 异常
ms.date: 10/04/2019
f1_keywords:
- bad_cast
- bad_cast_cpp
helpviewer_keywords:
- exceptions [C++], bad_cast
- bad_cast keyword [C++]
ms.assetid: 31eae1e7-d8d5-40a0-9fef-64a6a4fc9021
ms.openlocfilehash: 7384394fb53c6aa4bc009a903ba0ed22bf0ed0d6
ms.sourcegitcommit: c51b2c665849479fa995bc3323a22ebe79d9d7ce
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/07/2019
ms.locfileid: "71998782"
---
# <a name="bad_cast-exception"></a>bad_cast 异常

由于转换到引用类型失败， **dynamic_cast**运算符引发了**bad_cast**异常。

## <a name="syntax"></a>语法

```
catch (bad_cast)
   statement
```

## <a name="remarks"></a>备注

**Bad_cast**的接口是：

```cpp
class bad_cast : public exception
```

下面的代码包含引发**bad_cast**异常的失败**dynamic_cast**的示例。

```cpp
// expre_bad_cast_Exception.cpp
// compile with: /EHsc /GR
#include <typeinfo>
#include <iostream>

class Shape {
public:
   virtual void virtualfunc() const {}
};

class Circle: public Shape {
public:
   virtual void virtualfunc() const {}
};

using namespace std;
int main() {
   Shape shape_instance;
   Shape& ref_shape = shape_instance;
   try {
      Circle& ref_circle = dynamic_cast<Circle&>(ref_shape);
   }
   catch (bad_cast b) {
      cout << "Caught: " << b.what();
   }
}
```

引发此异常的原因是，被强制转换（形状）的对象不是派生自指定的强制转换类型（圆圈）。 若要避免此异常，请将下列声明添加到 `main`：

```cpp
Circle circle_instance;
Circle& ref_circle = circle_instance;
```

然后，在**try**块中反转强制转换的含义，如下所示：

```cpp
Shape& ref_shape = dynamic_cast<Shape&>(ref_circle);
```

## <a name="members"></a>成员

### <a name="constructors"></a>构造函数

|构造函数|描述|
|-|-|
|[bad_cast](#bad_cast)|`bad_cast` 类型的对象的构造函数。|

### <a name="functions"></a>Functions

|Functions|描述|
|-|-|
|[what](#what)|待定|

### <a name="operators"></a>运算符

|Operator|描述|
|-|-|
|[operator=](#op_eq)|赋值运算符，用于将一个 @no__t 0 对象分配给另一个。|

## <a name="bad_cast"></a>bad_cast

`bad_cast` 类型的对象的构造函数。

```cpp
bad_cast(const char * _Message = "bad cast");
bad_cast(const bad_cast &);
```

## <a name="op_eq"></a>operator =

赋值运算符，用于将一个 @no__t 0 对象分配给另一个。

```cpp
bad_cast& operator=(const bad_cast&) noexcept;
```

## <a name="what"></a>究竟

```cpp
const char* what() const noexcept override;
```

## <a name="see-also"></a>请参阅

[Dynamic_cast 运算符](../cpp/dynamic-cast-operator.md)\
[关键字](../cpp/keywords-cpp.md)\
[C++ 异常处理](../cpp/cpp-exception-handling.md)
