---
title: "编译器警告（等级 4）C4437 | Microsoft Docs"
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
ms.assetid: dc07e350-20eb-474c-a7ad-f841ae7ec339
caps.latest.revision: 3
caps.handback.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 4）C4437
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

从虚拟基“class1 " dynamic\_cast 到“class2”可能从上下文中失败编译使用 \/vd2 或定义“class2”使用 \#pragma 的 vtordisp \(2\) 实际上  
  
 默认情况下关闭此警告。  有关更多信息，请参见[默认情况下处于关闭状态的编译器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。  
  
 编译器遇到以下特性的 `dynamic_cast` 操作。  
  
-   转换是从基类指针到派生类的指针。  
  
-   派生类虚拟继承基类。  
  
-   派生类没有虚基类的 `vtordisp` 字段。  
  
-   转换在派生类的构造函数或析构函数，也不从派生类继承进一步的某些类不会找到 \(，编译器将发出警告 C4436。\)  
  
 警告意味着 `dynamic_cast` 可能执行不正确，如果对一部分构造的对象运行。出现此情况时，封闭函数从继承派生类在警告名为类的构造函数或析构函数时调用。如果警告在名为的派生类从不是进行进一步派生或封闭函数不在对象构造或析调用时，警告可以忽略。  
  
## 示例  
 下面的示例生成 C4437 并演示缺少`vtordisp` 字段会出现的生成的代码问题。  
  
```cpp  
// C4437.cpp  
// To see the warning and runtime assert, compile with: /W4  
// To eliminate the warning and assert, compile with: /W4 /vd2  
//       or compile with: /W4 /DFIX  
#pragma warning(default : 4437)  
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
        func();  
    }  
  
    void func()  
    {  
        A* a = static_cast<A*>(this);  
        B* b = dynamic_cast<B*>(a);     // C4437  
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
 [编译器警告（等级 1）C4436](../../error-messages/compiler-warnings/compiler-warning-level-1-c4436.md)