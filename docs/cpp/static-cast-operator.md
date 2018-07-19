---
title: static_cast 运算符 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- static_cast_cpp
dev_langs:
- C++
helpviewer_keywords:
- static_cast keyword [C++]
ms.assetid: 1f7c0c1c-b288-476c-89d6-0e2ceda5c293
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ad9af76787780ebe2a25b3fab46ce1951085b8e8
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2018
ms.locfileid: "37942580"
---
# <a name="staticcast-operator"></a>static_cast 运算符
将转换*表达式*为的类型*类型的 id，* 仅根据表达式中存在的类型。  
  
## <a name="syntax"></a>语法  
  
```  
static_cast <type-id> ( expression )   
```  
  
## <a name="remarks"></a>备注  
 在标准 C++ 中，不进行运行时类型检查来帮助确保转换的安全。 在 C++/CX 中，将执行编译时和运行时检查。 有关详细信息，请参阅[强制转换](casting.md)。  
  
 **Static_cast**运算符可用于操作，如指针转换为指向派生类的基类。 此类转换并非始终安全。  
  
 一般情况下使用**static_cast**时想要将数值数据类型，例如将枚举转换为整型或浮点型，而且您到整数数据类型的某些涉及在转换中。 **static_cast**转换不是安全性不如**dynamic_cast**的转换，因为**static_cast**不会不运行时类型检查，而**dynamic_cast**执行操作。 一个**dynamic_cast**到不明确的指针将失败，而**static_cast**返回好像没有问题，这可能很危险。 尽管**dynamic_cast**转换为更安全， **dynamic_cast**仅适用于指针或引用，而且运行时类型检查是一项开销。 有关详细信息，请参阅[dynamic_cast 运算符](../cpp/dynamic-cast-operator.md)。  
  
 在下面的示例中，因为 `D* pd2 = static_cast<D*>(pb);` 可能有不在 `D` 内的字段和方法，所以行 `B` 不安全。 但是，因为 `B* pb2 = static_cast<B*>(pd);` 始终包含所有 `D`，所以行 `B` 是安全的转换。  
  
```cpp 
// static_cast_Operator.cpp  
// compile with: /LD  
class B {};  
  
class D : public B {};  
  
void f(B* pb, D* pd) {  
   D* pd2 = static_cast<D*>(pb);   // Not safe, D can have fields  
                                   // and methods that are not in B.  
  
   B* pb2 = static_cast<B*>(pd);   // Safe conversion, D always  
                                   // contains all of B.  
}  
```  
  
 与此相反[dynamic_cast](../cpp/dynamic-cast-operator.md)，在进行任何运行时检查**static_cast**的转换`pb`。 由 `pb` 指向的对象可能不是 `D` 类型的对象，在这种情况下使用 `*pd2` 会是灾难性的。 例如，调用 `D` 类（而非 `B` 类）的成员函数可能会导致访问冲突。  
  
 **Dynamic_cast**并**static_cast**运算符移动整个类层次结构的指针。 但是， **static_cast**专门依赖使用 cast 语句中提供的信息，因此可能不安全。 例如：  
  
```cpp 
// static_cast_Operator_2.cpp  
// compile with: /LD /GR  
class B {  
public:  
   virtual void Test(){}  
};  
class D : public B {};  
  
void f(B* pb) {  
   D* pd1 = dynamic_cast<D*>(pb);  
   D* pd2 = static_cast<D*>(pb);  
}  
```  
  
 如果 `pb` 确实指向 `D` 类型的对象，则 `pd1` 和 `pd2` 将获取相同的值。 如果 `pb == 0`，它们也将获取相同的值。  
  
 如果`pb`指向类型的对象`B`而不适用于完整`D`类，则**dynamic_cast**将足以判断返回零。 但是， **static_cast**依赖于程序员的断言的`pb`指向类型的对象`D`并只返回一个指向应`D`对象。  
  
 因此， **static_cast**可以执行的逆函数隐式转换，这种情况下，则结果不确定。 它从左到程序员来验证的结果**static_cast**转换是安全。  
  
 该行为也适用于类以外的类型。 例如， **static_cast**可用于将转换到 int **char**。 但是，得到**char**可能没有足够的位来保存整个**int**值。 同样，它从左到程序员来验证的结果**static_cast**转换是安全。  
  
 **Static_cast**运算符还可用于执行任何隐式转换，包括标准转换和用户定义的转换。 例如：  
  
```cpp 
// static_cast_Operator_3.cpp  
// compile with: /LD /GR  
typedef unsigned char BYTE;  
  
void f() {  
   char ch;  
   int i = 65;  
   float f = 2.5;  
   double dbl;  
  
   ch = static_cast<char>(i);   // int to char  
   dbl = static_cast<double>(f);   // float to double  
   i = static_cast<BYTE>(ch);  
}  
```  
  
 **Static_cast**运算符可以显式将整数值转换为枚举类型。 如果整型值不在枚举值的范围内，生成的枚举值是不确定的。  
  
 **Static_cast**运算符将 null 指针值转换为目标类型的 null 指针值。  
  
 任何表达式可以显式转换为类型 void 通过**static_cast**运算符。 目标 void 类型可以选择性地包含**const**，**易失性**，或 **__unaligned**属性。  
  
 **Static_cast**运算符无法转换掉**const**，**易失性**，或者 **__unaligned**属性。 请参阅[const_cast 运算符](../cpp/const-cast-operator.md)有关删除这些属性的信息。  
  
 由于重定位垃圾回收器，使用顶部执行无检查的转换的危险**static_cast**仅在性能关键代码时应确定将正常工作。 如果必须使用**static_cast**在发布模式下，将其与[safe_cast](../windows/safe-cast-cpp-component-extensions.md)在调试版本中，以确保成功。  
  
## <a name="see-also"></a>请参阅  
 [强制转换运算符](../cpp/casting-operators.md)   
 [关键字](../cpp/keywords-cpp.md)