---
title: bad_cast 异常 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- bad_cast
- bad_cast_cpp
dev_langs:
- C++
helpviewer_keywords:
- exceptions [C++], bad_cast
- bad_cast keyword [C++]
ms.assetid: 31eae1e7-d8d5-40a0-9fef-64a6a4fc9021
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3bd5bb63e075303856d444cb08c2c1f3abe990b0
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46083933"
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
class bad_cast : public exception {
public:
   bad_cast(const char * _Message = "bad cast");
   bad_cast(const bad_cast &);
   virtual ~bad_cast();
};
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

## <a name="see-also"></a>请参阅

[dynamic_cast 运算符](../cpp/dynamic-cast-operator.md)<br/>
[关键字](../cpp/keywords-cpp.md)<br/>
[C++ 异常处理](../cpp/cpp-exception-handling.md)