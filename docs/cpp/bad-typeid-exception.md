---
title: bad_typeid 异常
ms.date: 11/04/2016
f1_keywords:
- bad_typeid
- bad_typeid_cpp
helpviewer_keywords:
- bad_typeid exception
- exceptions [C++], bad_typeid
ms.assetid: 5963ed58-4ede-4597-957d-f7bbd06299c2
ms.openlocfilehash: 0389a6db1249ad47d4ca5cc10003169933c7a5c3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392383"
---
# <a name="badtypeid-exception"></a>bad_typeid 异常

**Bad_typeid**引发异常[typeid 运算符](../cpp/typeid-operator.md)时的操作数**typeid**是 NULL 指针。

## <a name="syntax"></a>语法

```
catch (bad_typeid)
   statement
```

## <a name="remarks"></a>备注

接口**bad_typeid**是：

```cpp
class bad_typeid : public exception
{
public:
   bad_typeid(const char * _Message = "bad typeid");
   bad_typeid(const bad_typeid &);
   virtual ~bad_typeid();
};
```

下面的示例演示**typeid**运算符引发**bad_typeid**异常。

```cpp
// expre_bad_typeid.cpp
// compile with: /EHsc /GR
#include <typeinfo.h>
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

[运行时类型信息](../cpp/run-time-type-information.md)<br/>
[关键字](../cpp/keywords-cpp.md)