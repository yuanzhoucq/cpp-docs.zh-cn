---
title: bad_cast 异常
ms.date: 11/04/2016
f1_keywords:
- bad_cast
- bad_cast_cpp
helpviewer_keywords:
- exceptions [C++], bad_cast
- bad_cast keyword [C++]
ms.assetid: 31eae1e7-d8d5-40a0-9fef-64a6a4fc9021
ms.openlocfilehash: b40f64671e7c259b7dc04b31a11d20d0fc76c5c4
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/16/2019
ms.locfileid: "68242394"
---
# <a name="badcast-exception"></a>bad_cast 异常

**Bad_cast**引发异常**dynamic_cast**作为失败的强制转换为引用类型的结果的运算符。

## <a name="syntax"></a>语法

```
catch (bad_cast)
   statement
```

## <a name="remarks"></a>备注

接口**bad_cast**是：

```cpp
class bad_cast : public exception
```

下面的代码包含失败的示例**dynamic_cast** ，将引发**bad_cast**异常。

```cpp
// expre_bad_cast_Exception.cpp
// compile with: /EHsc /GR
#include <typeinfo.h>
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

由于强制转换的对象 (Shape) 不是派生自指定的强制转换类型 (Circle)，因此引发异常。 若要避免此异常，请将下列声明添加到 `main`：

```cpp
Circle circle_instance;
Circle& ref_circle = circle_instance;
```

然后反转中强制转换的意义**尝试**阻止按如下所示：

```cpp
Shape& ref_shape = dynamic_cast<Shape&>(ref_circle);
```

## <a name="members"></a>成员

### <a name="constructors"></a>构造函数

|构造函数|描述|
|-|-|
|[bad_cast](#bad_cast)|`bad_cast` 类型的对象的构造函数。|

### <a name="functions"></a>函数

|函数|描述|
|-|-|
|[what](#what)|待定|

### <a name="operators"></a>运算符

|运算符|描述|
|-|-|
|[operator=](#op_eq)|将分配一个赋值运算符`bad_cast`到另一个对象。|

## <a name="bad_cast"></a> bad_cast

`bad_cast` 类型的对象的构造函数。

```cpp
bad_cast(const char * _Message = "bad cast");
bad_cast(const bad_cast &);
```

## <a name="op_eq"></a> 运算符 =

将分配一个赋值运算符`bad_cast`到另一个对象。

```cpp
bad_cast& operator=(const bad_cast&) noexcept;
```

## <a name="what"></a> 什么

```cpp
const char* what() const noexcept override;
```

## <a name="see-also"></a>请参阅

[dynamic_cast 运算符](../cpp/dynamic-cast-operator.md)<br/>
[关键字](../cpp/keywords-cpp.md)<br/>
[C++ 异常处理](../cpp/cpp-exception-handling.md)