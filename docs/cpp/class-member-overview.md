---
title: "类成员概述 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- members, types of class members
- members
- class members, types of
- class members
ms.assetid: 8802cfa9-705d-4f37-acde-245d6838010c
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
ms.openlocfilehash: 0a5a62edf0e71b4fecf25cf10731af7d7c515da7
ms.contentlocale: zh-cn
ms.lasthandoff: 09/25/2017

---
# <a name="class-member-overview"></a>类成员概述
类或结构由其成员组成。 类的工作由其成员函数执行。 它所维持的状态存储在其数据成员中。 成员初始化的通过构造函数和清理工作，如释放的内存和释放资源可通过析构函数。 在 C++ 11 和更高版本中，数据成员可以（并且通常应该）在声明时初始化。  
  
## <a name="kinds-of-class-members"></a>类成员的种类  
 成员类别的完整列表如下：  
  
-   [特殊成员函数](special-member-functions.md)。  
  
-   [成员函数概述](overview-of-member-functions.md)。  
  
-   [数据成员](static-members-cpp.md)包括内置类型和其他用户定义的类型。  
  
-   运算符  
  
-   [嵌套类声明](nested-class-declarations.md)和。)  
  
-   [Unions](unions.md)  
  
-   [枚举](../cpp/enumerations-cpp.md)。  
  
-   [位域](../cpp/cpp-bit-fields.md)。  
  
-   [友元](../cpp/friend-cpp.md)。  
  
-   [别名和 typedef](../cpp/aliases-and-typedefs-cpp.md)。  
  
    > [!NOTE]
    >  前面的列表中包括友元，因为它们包含在类声明中。 但是，它们不是真正的类成员，因为它们不在类范围内。  
  
## <a name="example-class-declaration"></a>类声明示例  
 下面的示例显示了一个简单的类声明：  
  
```  
// TestRun.h  
  
class TestRun  
{  
    // Start member list.  
  
    //The class interface accessible to all callers.  
public:  
    // Use compiler-generated default constructor:  
    TestRun() = default;   
    // Don't generate a copy constructor:  
    TestRun(const TestRun&) = delete;    
    TestRun(std::string name);  
    void DoSomething();  
    int Calculate(int a, double d);  
    virtual ~TestRun();  
    enum class State { Active, Suspended };  
  
    // Accessible to this class and derived classes only.  
protected:  
    virtual void Initialize();  
    virtual void Suspend();  
    State GetState();  
  
    // Accessible to this class only.  
private:  
    // Default brace-initialization of instance members:  
    State _state{ State::Suspended };   
    std::string _testName{ "" };   
    int _index{ 0 };  
  
    // Non-const static member:  
    static int _instances;  
    // End member list.  
};  
  
// Define and initialize static member.  
int TestRun::_instances{ 0 };  
```  
  
## <a name="member-accessibility"></a>成员可访问性  
 在成员列表中声明类的成员。 类的成员列表中可能会分为任意数量的`private`，`protected`和**公共**部分使用称为访问说明符的关键字。  冒号**:**必须遵循访问说明符。  这些部分不需要是连续的，也就是说，这些关键字中的任何一个都可能在成员列表中多次出现。  关键字指定所有成员直到下一个访问说明符或右大括号的访问。 有关详细信息，请参阅[成员访问控制 （c + +）](../cpp/member-access-control-cpp.md)。  
  
## <a name="static-members"></a>静态成员  
 可将数据成员声明为静态，这表示类的所有对象都有权访问它的同一副本。 成员函数可能被声明为静态，在这种情况下它只能访问类的静态数据成员 (且不具有*这*指针)。 有关详细信息，请参阅[静态数据成员](../cpp/static-members-cpp.md)。  
  
## <a name="special-member-functions"></a>特殊成员函数  
 如果你并未在源代码中指定特殊成员函数，那么编译器自动提供的函数则为特殊成员函数。  
  
1.  默认构造函数  
  
2.  复制构造函数  
  
3.  **(C + + 11)**移动构造函数  
  
4.  复制赋值运算符  
  
5.  **(C + + 11)**移动赋值运算符  
  
6.  析构函数  
  
有关详细信息，请参阅[特殊成员函数](../cpp/special-member-functions.md)。
  
## <a name="memberwise-initialization"></a>按成员初始化  
 在 C++ 11 和更高版本中，非静态成员声明符可以包含初始值设定项。  
  
```  
  
class CanInit  
{  
public:  
    long num {7};       // OK in C++11  
    int k = 9;          // OK in C++11  
    static int i = 9; // Error: must be defined and initialized  
                      // outside of class declaration.  
  
    // initializes num to 7 and k to 9  
    CanInit(){}  
  
    // overwrites original initialized value of num:  
    CanInit(int val) : num(val) {}  
};  
int main()  
{  
}  
```  
  
 如果在构造函数中对一个成员分配了一个值，则该值将覆盖声明时用于初始化该成员的值。  
  
 对于给定类类型的所有对象，只有一个静态数据成员的共享副本。 必须在文件范围内定义静态数据成员并可在此范围内将其初始化。 (有关静态数据成员的详细信息，请参阅[静态数据成员](../cpp/static-members-cpp.md)。)以下示例演示如何执行这些初始化：  
  
```  
// class_members2.cpp  
class CanInit2  
{  
public:  
    CanInit2() {} // Initializes num to 7 when new objects of type   
                 //  CanInit are created.  
    long     num {7};  
    static int i;  
    static int j;  
};  
  
// At file scope:  
  
// i is defined at file scope and initialized to 15.  
// The initializer is evaluated in the scope of CanInit.  
int CanInit2::i = 15;  
  
// The right side of the initializer is in the scope   
// of the object being initialized  
int CanInit2::j = i;  
```  
  
> [!NOTE]
>  类名 `CanInit2` 的前面必须有 `i` 以指定所定义的 `i` 是类 `CanInit2` 的成员。  
  
## <a name="see-also"></a>另请参阅  
 [类和结构](../cpp/classes-and-structs-cpp.md)

