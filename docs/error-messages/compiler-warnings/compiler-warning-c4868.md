---
title: "编译器警告 C4868 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4868
ms.assetid: fc6aa7e5-34dd-4ec2-88bd-16e430361dc7
caps.latest.revision: 4
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 26031e1ac6f39d745a772e1becf3f817213a59d8
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-c4868"></a>编译器警告 C4868
file(line_number) 编译器不会强制从左到右的计算顺序按大括号内的初始值设定项列表  
  
 大括号内的初始值设定项列表中的元素是从左到右的顺序进行计算。 有两种情况下，在其中编译器就无法保证此顺序︰ 第一种是通过值; 如果传递的对象时的一些元素第二个是使用编译时`/clr`和的某些元素对象的字段或数组元素。 当编译器无法保证从左到右评估它将发出警告 C4868。  
  
 已经为 Visual c + + 2015 Update 2 的编译器一致性工作可以生成此警告。 现在，在 Visual c + + 2015 Update 2 之前编译的代码将生成 C4868。  
  
 默认情况下，此警告处于关闭状态。 使用`/Wall`来激活此警告。  
  
 要解决此警告，请首先考虑初始值设定项列表元素的从左到右评估是否是必需的例如求值的元素时可能会产生按顺序排列的副作用。 在许多情况下，元素的计算顺序没有明显的影响。  
  
 如果求值的顺序必须是从左到右，请考虑是否可以元素通过引用来传递 （常数） 相反。 此更改消除了下面的代码示例中的警告。  
  
## <a name="example"></a>示例  
 下面的示例生成 C4868。  
  
```  
// C4868.cpp  
// compile with: /c /Wall  
#include <cstdio>  
  
class HasCopyConstructor  
{  
public:  
    int x;  
  
    HasCopyConstructor(int x): x(x) {}  
  
    HasCopyConstructor(const HasCopyConstructor& h): x(h.x)  
    {  
        printf("Constructing %d\n", h.x);  
    }  
};  
  
class TripWarning4868  
{  
public:  
    // note that taking "HasCopyConstructor" parameters by-value will trigger copy-construction.  
    TripWarning4868(HasCopyConstructor a, HasCopyConstructor b) {}  
  
    // This variation will not trigger the warning:  
    // TripWarning4868(const HasCopyConstructor& a, const HasCopyConstructor& b) {}  
};  
  
int main()  
{  
    HasCopyConstructor a{1};  
    HasCopyConstructor b{2};  
  
    // the warning will indicate the below line, the usage of the braced initializer list.  
    TripWarning4868 warningOnThisLine{a, b};  
};  
```
