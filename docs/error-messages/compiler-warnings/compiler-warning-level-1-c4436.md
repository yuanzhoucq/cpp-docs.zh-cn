---
title: "编译器警告（等级 1）C4436 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
dev_langs: 
  - "C++"
ms.assetid: 2b54a1fc-c9c6-4cc9-90be-faa44fc715d5
caps.latest.revision: 2
caps.handback.revision: 2
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 1）C4436
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

从虚拟基“class1 " dynamic\_cast 到“class2”在构造函数或析构函数可能失败。部分构造的对象编译使用 \/vd2 或定义“class2”使用 \#pragma 的 vtordisp \(2\) 实际上  
  
 编译器遇到以下特性的 `dynamic_cast` 操作。  
  
-   转换是从基类指针到派生类的指针。  
  
-   派生类虚拟继承基类。  
  
-   派生类没有虚基类的 `vtordisp` 字段。  
  
-   在派生类的构造函数或析构函数中转换，或在派生类的继承的一些类中。  
  
 警告意味着 `dynamic_cast` 可能执行不正确，如果对一部分构造的对象运行。如果导出的构造函数\/析构函数运行在某些进一步派生对象的子对象，运行该操作。若警告中命名的派生类从没有进行进一步派生，警告可以忽略。  
  
## 示例  
 下面的示例生成 C4436 并演示缺少`vtordisp` 字段会出现的生成的代码问题。  
  
```cpp  
// C4436.cpp  
// To see the warning and runtime assert, compile with: /W1  
// To eliminate the warning and assert, compile with: /W1 /vd2  
//       or compile with: /W1 /DFIX  
#include <cassert>  
  
struct A  
{  
public:  
    virtual ~A() {}  
};  
  
#if defined(FIX)  
#pragma vtordisp(push, 2)  
#endif  
struct B : virtual A  
{  
    B()  
    {  
        A* a = static_cast<A*>(this);  
        B* b = dynamic_cast<B*>(a);     // C4436  
        assert(this == b);              // assert unless compiled with /vd2  
    }  
};  
#if defined(FIX)  
#pragma vtordisp(pop)  
#endif  
  
struct C : B  
{  
    int i;  
};  
  
int main()  
{  
    C c;  
}  
```  
  
## 请参阅  
 [dynamic\_cast 运算符](../../cpp/dynamic-cast-operator.md)   
 [vtordisp](../../preprocessor/vtordisp.md)   
 [编译器警告（等级 4）C4437](../../error-messages/compiler-warnings/compiler-warning-level-4-c4437.md)