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
ms.openlocfilehash: 55718522bdbf618fb656eedc5c6afd59bfcaca08
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/01/2018
ms.locfileid: "39409002"
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
 [运行时类型信息](../cpp/run-time-type-information.md)   
 [关键字](../cpp/keywords-cpp.md)