---
title: bad_typeid 异常
ms.date: 10/04/2019
f1_keywords:
- bad_typeid
- bad_typeid_cpp
helpviewer_keywords:
- bad_typeid exception
- exceptions [C++], bad_typeid
ms.assetid: 5963ed58-4ede-4597-957d-f7bbd06299c2
ms.openlocfilehash: 3e01f97c67803408c9ce5bf056e3e9ed4746d259
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229163"
---
# <a name="bad_typeid-exception"></a>bad_typeid 异常

如果的操作数为 NULL 指针，则[typeid 运算符](../cpp/typeid-operator.md)引发**bad_typeid**异常 **`typeid`** 。

## <a name="syntax"></a>语法

```
catch (bad_typeid)
   statement
```

## <a name="remarks"></a>备注

**Bad_typeid**的接口是：

```cpp
class bad_typeid : public exception
{
public:
   bad_typeid();
   bad_typeid(const char * _Message = "bad typeid");
   bad_typeid(const bad_typeid &);
   virtual ~bad_typeid();

   bad_typeid& operator=(const bad_typeid&);
   const char* what() const;
};
```

下面的示例演示了 **`typeid`** 引发**bad_typeid**异常的运算符。

```cpp
// expre_bad_typeid.cpp
// compile with: /EHsc /GR
#include <typeinfo>
#include <iostream>

class A{
public:
   // object for class needs vtable
   // for RTTI
   virtual ~A();
};

using namespace std;
int main() {
A* a = NULL;

try {
   cout << typeid(*a).name() << endl;  // Error condition
   }
catch (bad_typeid){
   cout << "Object is NULL" << endl;
   }
}
```

## <a name="output"></a>Output

```Output
Object is NULL
```

## <a name="see-also"></a>请参阅

[运行时类型信息](../cpp/run-time-type-information.md)\
[关键字](../cpp/keywords-cpp.md)
