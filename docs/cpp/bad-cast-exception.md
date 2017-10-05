---
title: "bad_cast 异常 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- bad_cast
- bad_cast_cpp
dev_langs:
- C++
helpviewer_keywords:
- exceptions, bad_cast
- bad_cast keyword [C++]
ms.assetid: 31eae1e7-d8d5-40a0-9fef-64a6a4fc9021
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 70758ca099853f94ad06b8a9f5029203a480a772
ms.contentlocale: zh-cn
ms.lasthandoff: 09/25/2017

---
# <a name="badcast-exception"></a>bad_cast 异常
由于强制转换为引用类型失败，`bad_cast` 运算符引发 `dynamic_cast` 异常。  
  
## <a name="syntax"></a>语法  
  
```  
catch (bad_cast)  
   statement  
```  
  
## <a name="remarks"></a>备注  
 `bad_cast` 的接口为：  
  
```  
class bad_cast : public exception {  
public:  
   bad_cast(const char * _Message = "bad cast");  
   bad_cast(const bad_cast &);  
   virtual ~bad_cast();  
};  
```  
  
 以下代码包含失败的 `dynamic_cast` 引发 `bad_cast` 异常的示例。  
  
```  
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
  
```  
Circle circle_instance;  
Circle& ref_circle = circle_instance;  
```  
  
 然后在 `try` 块中反转强制转换的意义，如下所示：  
  
```  
Shape& ref_shape = dynamic_cast<Shape&>(ref_circle);  
```  
  
## <a name="see-also"></a>另请参阅  
 [dynamic_cast 运算符](../cpp/dynamic-cast-operator.md)   
 [关键字](../cpp/keywords-cpp.md)   
 [C++ 异常处理](../cpp/cpp-exception-handling.md)
