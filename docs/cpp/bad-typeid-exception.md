---
title: bad_typeid 异常 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- bad_typeid
- bad_typeid_cpp
dev_langs:
- C++
helpviewer_keywords:
- bad_typeid exception
- exceptions [C++], bad_typeid
ms.assetid: 5963ed58-4ede-4597-957d-f7bbd06299c2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9cc93ab5a0f2d7fce12e926d571881ccb9c070fd
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46092201"
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

## <a name="output"></a>输出

```Output
Object is NULL
```

## <a name="see-also"></a>请参阅

[运行时类型信息](../cpp/run-time-type-information.md)<br/>
[关键字](../cpp/keywords-cpp.md)