---
title: "STL/CLR 容器 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "容器, STL/CLR"
  - "STL/CLR, 容器"
ms.assetid: 34ca8031-2041-46b9-aed9-29082d1972ea
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# STL/CLR 容器
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

STL\/CLR 库在标准 C\+\+ 库中找到具有相同容器，但在 .NET Framework 的托管环境中运行。  如果您已经熟悉标准模板库 \(STL\) \(STL\)，STL\/CLR 的最佳方式是继续使用已开发的，则代码升级面向公共语言运行时后 \(CLR\) 的技能。  
  
 本文档提供的概述STL\/CLR 容器，例如容器元素的要求，您可以插入到容器元素的所有权发出类型与容器中的元素。  在适用地方本机和标准模板库 \(STL\) STL\/CLR 之间差异会提到。  
  
## 容器元素的要求  
 所有元素插入 STL 容器必须遵循某些指南。  有关详细信息，请参阅[STL\/CLR 容器元素的要求](../dotnet/requirements-for-stl-clr-container-elements.md)。  
  
## 有效元素的容器  
 STL\/CLR 容器可容纳元素为两种类型之一：  
  
-   转换为引用类型。  
  
-   引用类型。  
  
-   不能装箱的值类型。  
  
 将不能插入装箱值类型到STL\/CLR任何容器。  
  
### 转换为引用类型。  
 可以插入句柄引用类型到STL\/CLR 容器。  面向 CLR 在 C\+\+ 的句柄很类似于本机 C\+\+ 的指针。  有关详细信息，请参阅[对象句柄运算符 \(^\)](../windows/handle-to-object-operator-hat-cpp-component-extensions.md)。  
  
#### 示例  
 下面的示例演示如何插入句柄到 Employee 对象到 [cliext::set](../dotnet/set-stl-clr.md)。  
  
```  
// cliext_container_valid_reference_handle.cpp  
// compile with: /clr  
  
#include <cliext/set>  
  
using namespace cliext;  
using namespace System;  
  
ref class Employee  
{  
public:  
    // STL containers might require a public constructor, so it  
    // is a good idea to define one.  
    Employee() :  
        name(nullptr),  
        employeeNumber(0) { }  
  
    // All STL containers require a public copy constructor.  
    Employee(const Employee% orig) :  
        name(orig.name),  
        employeeNumber(orig.employeeNumber) { }  
  
    // All STL containers require a public assignment operator.  
    Employee% operator=(const Employee% orig)  
    {  
        if (this != %orig)  
        {  
            name = orig.name;  
            employeeNumber = orig.employeeNumber;  
        }  
  
        return *this;  
    }  
  
    // All STL containers require a public destructor.  
    ~Employee() { }  
  
    // Associative containers such as maps and sets  
    // require a comparison operator to be defined  
    // to determine proper ordering.  
    bool operator<(const Employee^ rhs)  
    {  
        return (employeeNumber < rhs->employeeNumber);  
    }  
  
    // The employee's name.  
    property String^ Name  
    {  
        String^ get() { return name; }  
        void set(String^ value) { name = value; }  
    }  
  
    // The employee's employee number.  
    property int EmployeeNumber  
    {  
        int get() { return employeeNumber; }  
        void set(int value) { employeeNumber = value; }  
    }  
  
private:  
    String^ name;  
    int employeeNumber;  
};  
  
int main()  
{  
    // Create a new employee object.  
    Employee^ empl1419 = gcnew Employee();  
    empl1419->Name = L"Darin Lockert";  
    empl1419->EmployeeNumber = 1419;  
  
    // Add the employee to the set of all employees.  
    set<Employee^>^ emplSet = gcnew set<Employee^>();  
    emplSet->insert(empl1419);  
  
    // List all employees of the company.  
    for each (Employee^ empl in emplSet)  
    {  
        Console::WriteLine("Employee Number {0}: {1}",  
            empl->EmployeeNumber, empl->Name);  
    }  
  
    return 0;  
}  
```  
  
### 引用类型  
 插入引用类型 \(而不是引用类型的句柄\)到STL\/CLR 容器 也是可能的。  此处的主要差异是，当容器类型引用时，删除析构函数需要调用容器的任何元素。  在容器被引用的类型句柄，这些元素的析构函数将不被调用。  
  
#### 示例  
 下面的示例说明如何在应用程序中插入Employee对象到`cliext::set`。  
  
```  
// cliext_container_valid_reference.cpp  
// compile with: /clr  
  
#include <cliext/set>  
  
using namespace cliext;  
using namespace System;  
  
ref class Employee  
{  
public:  
    // STL containers might require a public constructor, so it  
    // is a good idea to define one.  
    Employee() :  
        name(nullptr),  
        employeeNumber(0) { }  
  
    // All STL containers require a public copy constructor.  
    Employee(const Employee% orig) :  
        name(orig.name),  
        employeeNumber(orig.employeeNumber) { }  
  
    // All STL containers require a public assignment operator.  
    Employee% operator=(const Employee% orig)  
    {  
        if (this != %orig)  
        {  
            name = orig.name;  
            employeeNumber = orig.employeeNumber;  
        }  
  
        return *this;  
    }  
  
    // All STL containers require a public destructor.  
    ~Employee() { }  
  
    // Associative containers such as maps and sets  
    // require a comparison operator to be defined  
    // to determine proper ordering.  
    bool operator<(const Employee^ rhs)  
    {  
        return (employeeNumber < rhs->employeeNumber);  
    }  
  
    // The employee's name.  
    property String^ Name  
    {  
        String^ get() { return name; }  
        void set(String^ value) { name = value; }  
    }  
  
    // The employee's employee number.  
    property int EmployeeNumber  
    {  
        int get() { return employeeNumber; }  
        void set(int value) { employeeNumber = value; }  
    }  
  
private:  
    String^ name;  
    int employeeNumber;  
};  
  
int main()  
{  
    // Create a new employee object.  
    Employee empl1419;  
    empl1419.Name = L"Darin Lockert";  
    empl1419.EmployeeNumber = 1419;  
  
    // Add the employee to the set of all employees.  
    set<Employee>^ emplSet = gcnew set<Employee>();  
    emplSet->insert(empl1419);  
  
    // List all employees of the company.  
    for each (Employee^ empl in emplSet)  
    {  
        Console::WriteLine("Employee Number {0}: {1}",  
            empl->EmployeeNumber, empl->Name);  
    }  
  
    return 0;  
}  
```  
  
### 不能装箱的值类型。  
 您还可以插入已装箱的值类型到STL\/CLR 容器。  已装箱的值类型 *未装箱* 到引用类型的值类型。  
  
 值类型元素可以是任何标准值类型，如 `int`，也可以是一个用户定义的值类型，例如 `value class`。  有关更多信息，请参阅[类和结构 \(托管\)](../windows/classes-and-structs-cpp-component-extensions.md)。  
  
#### 示例  
 以下示例通过值类型 Employee 类修改第一个示例。  此值然后类型插入 `cliext::set` 正值在第一个示例中。  
  
```  
// cliext_container_valid_valuetype.cpp  
// compile with: /clr  
  
#include <cliext/set>  
  
using namespace cliext;  
using namespace System;  
  
value class Employee  
{  
public:  
    // Associative containers such as maps and sets  
    // require a comparison operator to be defined  
    // to determine proper ordering.  
    bool operator<(const Employee^ rhs)  
    {  
        return (employeeNumber < rhs->employeeNumber);  
    }  
  
    // The employee's name.  
    property String^ Name  
    {  
        String^ get() { return name; }  
        void set(String^ value) { name = value; }  
    }  
  
    // The employee's employee number.  
    property int EmployeeNumber  
    {  
        int get() { return employeeNumber; }  
        void set(int value) { employeeNumber = value; }  
    }  
  
private:  
    String^ name;  
    int employeeNumber;  
};  
  
int main()  
{  
    // Create a new employee object.  
    Employee empl1419;  
    empl1419.Name = L"Darin Lockert";  
    empl1419.EmployeeNumber = 1419;  
  
    // Add the employee to the set of all employees.  
    set<Employee>^ emplSet = gcnew set<Employee>();  
    emplSet->insert(empl1419);  
  
    // List all employees of the company.  
    for each (Employee empl in emplSet)  
    {  
        Console::WriteLine("Employee Number {0}: {1}",  
            empl.EmployeeNumber, empl.Name);  
    }  
  
    return 0;  
}  
```  
  
 如果您尝试插入句柄值类型到容器，[编译器错误 C3225](../error-messages/compiler-errors-2/compiler-error-c3225.md) 生成。  
  
### 性能和内存问题  
 在确定使用句柄引用类型或值类型作为容器元素时，您必须考虑多个因素。  如果您决定使用值类型元素的副本，请确保每次将元素粘贴到容器中。  对于小的对象，这应不会成为问题，但是，如果插入的对象很大时，性能可能大大影响。  此外，如果利用值类型，同时存储多种容器的元素是不可能的，因为的每个容器都有其自己的元素副本。  
  
 如果您决定使用句柄引用类型，性能可能会增加，因为元素副本是不必要的，因为会在容器中插入。  同样，不同的是具有值类型，同一元素可以存在多个容器。  但是，其中如果您决定使用句柄，必须注意确保句柄是否有效，并且确保它引用的对象在程序的其他地方未删除。  
  
## 使用容器所属权的问题  
 STL\/CLR 在工作的容器上值语义。  在将元素插入到容器时，该副本粘贴元素。  如果要获取与引用的语义，可插入对象的句柄，而不是对象。  
  
 当您调用或被清除对容器的方法处理对象时，句柄引用的对象不会从内存中释放。  你必须显式删除对象，或者一旦确定不再使用对象请允许垃圾回收器能够释放内存，因为这些对象位于托管堆。  
  
## 请参阅  
 [标准模板库](../misc/standard-template-library.md)