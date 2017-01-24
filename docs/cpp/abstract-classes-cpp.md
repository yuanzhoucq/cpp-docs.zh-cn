---
title: "抽象类 (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "抽象类"
  - "基类, 抽象类"
  - "类 [C++], abstract"
  - "派生类, 抽象类"
ms.assetid: f0c5975b-39de-4d68-9640-6ce57f4632e6
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 抽象类 (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

抽象类作为可从中派生更具体的类的一般概念的表达。  您不能创建抽象类类型的对象；但可以使用指向抽象类类型的指针和对它们的引用。  
  
 包含至少一个纯虚函数的类被视为抽象类。  派生自抽象类的类必须实现纯虚函数或者它们必须也是抽象类。  
  
 可使用 *pure\-specifier* 语法（在[类协议实现](http://msdn.microsoft.com/zh-cn/a319f1b3-05e8-400e-950a-1ca6eb105ab5)中描述）将虚函数声明为“纯”虚函数。  请考虑[虚函数](../cpp/virtual-functions.md)中所述的示例。  类 `Account` 的用途是提供通用功能，但 `Account` 类型的对象太通用，因此没什么用。  因此，`Account` 是抽象类的很合适的候选项：  
  
```  
// deriv_AbstractClasses.cpp  
// compile with: /LD  
class Account {  
public:  
   Account( double d );   // Constructor.  
   virtual double GetBalance();   // Obtain balance.  
   virtual void PrintBalance() = 0;   // Pure virtual function.  
private:  
    double _balance;  
};  
  
```  
  
 此声明与上一个声明的唯一区别是，`PrintBalance` 是用 pure 说明符 \(`= 0`\) 声明的。  
  
## 抽象类限制  
 抽象类不能用于：  
  
-   变量或成员数据  
  
-   参数类型  
  
-   函数返回类型  
  
-   显式转换的类型  
  
 另一个限制是，如果抽象类的构造函数调用一个纯虚函数，无论是直接还是间接方式，则结果都是不确定的。  但是，抽象类的构造函数和析构函数都可以调用其他成员函数。  
  
 可以为抽象类定义纯虚函数，但是只能通过使用以下语法直接调用：  
  
 *abstract\-class\-name* `::` *function\-name***\( \)**  
  
 这有助于设计基类包括纯虚析构函数的类层次结构，因为在销毁对象的过程中始终会调用基类析构函数。  请看下面的示例：  
  
```  
// Declare an abstract base class with a pure virtual destructor.  
// deriv_RestrictionsonUsingAbstractClasses.cpp  
class base {  
public:  
    base() {}  
    virtual ~base()=0;  
};  
  
// Provide a definition for destructor.  
base::~base() {}  
  
class derived:public base {  
public:  
    derived() {}  
    ~derived(){}  
};  
  
int main() {  
    derived *pDerived = new derived;  
    delete pDerived;  
}  
```  
  
 删除 `pDerived` 指向的对象时，将调用类 `derived` 的析构函数，然后调用类 `base` 的析构函数。  纯虚函数的空实现确保至少函数的某个实现存在。  
  
> [!NOTE]
>  在前面的示例中，纯虚函数 `base::~base` 是从 `derived::~derived` 隐式调用的。  还可使用完全限定的成员函数名称显式调用纯虚函数。  
  
## 请参阅  
 [继承](../cpp/inheritance-cpp.md)