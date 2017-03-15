---
title: "虚函数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "派生类, 虚函数"
  - "函数 [C++], 虚函数"
  - "虚函数"
ms.assetid: b3e1ed88-2a90-4af8-960a-16f47deb3452
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# 虚函数
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

虚函数是应在派生类中重新定义的成员函数。  当使用指针或对基类的引用来引用派生的类对象时，可以为该对象调用虚函数并执行该函数的派生类版本。  
  
 虚函数确保为该对象调用正确的函数，这与用于进行函数调用的表达式无关。  
  
 假定基类包含声明为 [virtual](../cpp/virtual-cpp.md) 的函数，并且派生类定义了相同的函数。  为派生类的对象调用派生类中的函数，即使它是使用指针或对基类的引用来调用的。  以下示例显示了一个基类，它提供了 `PrintBalance` 函数和两个派生类的实现  
  
```  
// deriv_VirtualFunctions.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
class Account {  
public:  
   Account( double d ) { _balance = d; }  
   virtual double GetBalance() { return _balance; }  
   virtual void PrintBalance() { cerr << "Error. Balance not available for base type." << endl; }  
private:  
    double _balance;  
};  
  
class CheckingAccount : public Account {  
public:  
   CheckingAccount(double d) : Account(d) {}  
   void PrintBalance() { cout << "Checking account balance: " << GetBalance() << endl; }  
};  
  
class SavingsAccount : public Account {  
public:  
   SavingsAccount(double d) : Account(d) {}  
   void PrintBalance() { cout << "Savings account balance: " << GetBalance(); }  
};  
  
int main() {  
   // Create objects of type CheckingAccount and SavingsAccount.  
   CheckingAccount *pChecking = new CheckingAccount( 100.00 ) ;  
   SavingsAccount  *pSavings  = new SavingsAccount( 1000.00 );  
  
   // Call PrintBalance using a pointer to Account.  
   Account *pAccount = pChecking;  
   pAccount->PrintBalance();  
  
   // Call PrintBalance using a pointer to Account.  
   pAccount = pSavings;  
   pAccount->PrintBalance();     
}  
```  
  
 在前面的代码中，对 `PrintBalance` 的调用是相同的，`pAccount` 所指向的对象除外。  由于 `PrintBalance` 是虚拟的，因此将调用为每个对象定义的函数版本。  派生类 `PrintBalance` 和 `CheckingAccount` 中的 `SavingsAccount` 函数“重写”基类 `Account` 中的函数。  
  
 如果声明的类不提供 `PrintBalance` 函数的重写实现，则使用基类 `Account` 中的默认实现。  
  
 派生类中的函数仅在基类中的虚函数的类型相同时重写这些虚函数。  派生类中的函数不能只是与其返回类型中的基类的虚函数不同；参数列表也必须不同。  
  
 当使用指针或引用调用函数时，以下规则将适用：  
  
-   根据为其调用的对象的基本类型来解析对虚函数的调用。  
  
-   根据指针或引用的类型来解析对非虚函数的调用。  
  
 以下示例说明在通过指针调用时虚函数和非虚函数的行为：  
  
```  
// deriv_VirtualFunctions2.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
class Base {  
public:  
   virtual void NameOf();   // Virtual function.  
   void InvokingClass();   // Nonvirtual function.  
};  
  
// Implement the two functions.  
void Base::NameOf() {  
   cout << "Base::NameOf\n";  
}  
  
void Base::InvokingClass() {  
   cout << "Invoked by Base\n";  
}  
  
class Derived : public Base {  
public:  
   void NameOf();   // Virtual function.  
   void InvokingClass();   // Nonvirtual function.  
};  
  
// Implement the two functions.  
void Derived::NameOf() {  
   cout << "Derived::NameOf\n";  
}  
  
void Derived::InvokingClass() {  
   cout << "Invoked by Derived\n";  
}  
  
int main() {  
   // Declare an object of type Derived.  
   Derived aDerived;  
  
   // Declare two pointers, one of type Derived * and the other  
   //  of type Base *, and initialize them to point to aDerived.  
   Derived *pDerived = &aDerived;  
   Base    *pBase    = &aDerived;  
  
   // Call the functions.  
   pBase->NameOf();           // Call virtual function.  
   pBase->InvokingClass();    // Call nonvirtual function.  
   pDerived->NameOf();        // Call virtual function.  
   pDerived->InvokingClass(); // Call nonvirtual function.  
}  
```  
  
### 输出  
  
```  
Derived::NameOf  
Invoked by Base  
Derived::NameOf  
Invoked by Derived  
```  
  
 请注意，无论 `NameOf` 函数是通过指向 `Base` 的指针还是通过指向 `Derived` 的指针进行调用，它都会调用 `Derived` 的函数。  它调用 `Derived` 的函数，因为 `NameOf` 是虚函数，并且 `pBase` 和 `pDerived` 都指向类型 `Derived` 的对象。  
  
 由于仅为类类型的对象调用虚函数，因此不能将全局函数或静态函数声明为 **virtual**。  
  
 在派生类中声明重写函数时可使用 **virtual** 关键字，但它不是必需的；虚函数的重写始终是虚拟的。  
  
 必须定义基类中的虚函数，除非使用 *pure\-specifier* 声明它们。  （有关纯虚函数的详细信息，请参阅[抽象类](../cpp/abstract-classes-cpp.md)。）  
  
 可通过使用范围解析运算符 \(`::`\) 显式限定函数名称来禁用虚函数调用机制。  考虑先前涉及 `Account` 类的示例。  若要调用基类中的 `PrintBalance`，请使用如下所示的代码：  
  
```  
CheckingAccount *pChecking = new CheckingAccount( 100.00 );  
  
pChecking->Account::PrintBalance();  //  Explicit qualification.  
  
Account *pAccount = pChecking;  // Call Account::PrintBalance  
  
pAccount->Account::PrintBalance();   //  Explicit qualification.  
```  
  
 在前面的示例中，对 `PrintBalance` 的调用将禁用虚函数调用机制。  
  
## 请参阅  
 [对虚函数的访问](../misc/access-to-virtual-functions.md)