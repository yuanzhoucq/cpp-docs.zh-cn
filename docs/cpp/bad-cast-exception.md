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
ms.openlocfilehash: 11b42c9e6210c2432563bba43c55517abd4265fe
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/20/2019
ms.locfileid: "74245954"
---
# <a name="bad_cast-exception"></a>bad_cast 异常

由于转换为引用类型失败的结果， **dynamic_cast**运算符引发**bad_cast**异常。

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

## <a name="members"></a>Members

### <a name="constructors"></a>构造函数

|构造函数|说明|
|-|-|
|[bad_cast](#bad_cast)|`bad_cast` 类型的对象的构造函数。|

### <a name="functions"></a>函数

|函数|说明|
|-|-|
|[究竟](#what)|TBD|

### <a name="operators"></a>运算符

|运算符|说明|
|-|-|
|[operator=](#op_eq)|一个赋值运算符，用于将一个 `bad_cast` 对象分配给另一个对象。|

## <a name="bad_cast"></a>bad_cast

`bad_cast` 类型的对象的构造函数。

```cpp
bad_cast(const char * _Message = "bad cast");
bad_cast(const bad_cast &);
```

## <a name="op_eq"></a>operator =

一个赋值运算符，用于将一个 `bad_cast` 对象分配给另一个对象。

```cpp
bad_cast& operator=(const bad_cast&) noexcept;
```

## <a name="what"></a>究竟

```cpp
const char* what() const noexcept override;
```

## <a name="see-also"></a>另请参阅

[Dynamic_cast 运算符](../cpp/dynamic-cast-operator.md)\
[关键字](../cpp/keywords-cpp.md)\
[异常C++和错误处理的新式最佳实践](../cpp/errors-and-exception-handling-modern-cpp.md)
