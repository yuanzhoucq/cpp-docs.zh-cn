---
title: STL/CLR 容器
ms.date: 09/18/2018
ms.topic: reference
helpviewer_keywords:
- STL/CLR, containers
- containers, STL/CLR
ms.assetid: 34ca8031-2041-46b9-aed9-29082d1972ea
ms.openlocfilehash: dc2e5ce3263c61839a1ba434ab0d2a39e6a9078f
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "58774537"
---
# <a name="stlclr-containers"></a>STL/CLR 容器

STL/CLR 库包含类似于中的容器的C++标准库，但它在.NET Framework 的托管环境中运行。 不进行更新的实际C++标准库和维护的旧版支持。

本文档提供 STL/CLR 中的容器的概述，例如容器元素的需求、可以插入到容器中的元素类型以及容器中的元素的所有权问题。 在适当的位置，本机之间的差异C++标准库和 STL/CLR 所述。

## <a name="requirements-for-container-elements"></a>容器元素的需求

插入到 STL/CLR 容器的所有元素必须都遵循某些准则。 有关详细信息，请参阅[STL/CLR 容器元素的需求](../dotnet/requirements-for-stl-clr-container-elements.md)。

## <a name="valid-container-elements"></a>有效的容器元素

STL/CLR 容器可容纳以下两种元素类型之一：

- 指向引用类型的句柄。

- 引用类型。

- 未装箱的值类型。

您不能将装箱的值类型插入到任何 STL/CLR 容器中。

### <a name="handles-to-reference-types"></a>指向引用类型的句柄

您可以将指向引用类型的句柄插入到 STL/CLR 容器中。 C++ 中面向 CLR 的句柄与 C++ 中的指针类似。 有关详细信息，请参阅[句柄对象运算符 (^)](../extensions/handle-to-object-operator-hat-cpp-component-extensions.md)。

#### <a name="example"></a>示例

下面的示例演示如何插入到 Employee 对象的句柄[cliext:: set](../dotnet/set-stl-clr.md)。

```
// cliext_container_valid_reference_handle.cpp
// compile with: /clr

#include <cliext/set>

using namespace cliext;
using namespace System;

ref class Employee
{
public:
    // STL/CLR containers might require a public constructor, so it
    // is a good idea to define one.
    Employee() :
        name(nullptr),
        employeeNumber(0) { }

    // All STL/CLR containers require a public copy constructor.
    Employee(const Employee% orig) :
        name(orig.name),
        employeeNumber(orig.employeeNumber) { }

    // All STL/CLR containers require a public assignment operator.
    Employee% operator=(const Employee% orig)
    {
        if (this != %orig)
        {
            name = orig.name;
            employeeNumber = orig.employeeNumber;
        }

        return *this;
    }

    // All STL/CLR containers require a public destructor.
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

### <a name="reference-types"></a>引用类型

还可以将引用类型（而不是指向引用类型的句柄）插入到 STL/CLR 容器中。 此处的主要差异是，当删除类型引用的容器时，将为容器中的所有元素调用析构函数。 在指向引用类型的句柄的容器中，则不会调用这些元素的析构函数。

#### <a name="example"></a>示例

以下示例演示了如何将 Employee 对象插入到 `cliext::set` 中。

```
// cliext_container_valid_reference.cpp
// compile with: /clr

#include <cliext/set>

using namespace cliext;
using namespace System;

ref class Employee
{
public:
    // STL/CLR containers might require a public constructor, so it
    // is a good idea to define one.
    Employee() :
        name(nullptr),
        employeeNumber(0) { }

    // All STL/CLR containers require a public copy constructor.
    Employee(const Employee% orig) :
        name(orig.name),
        employeeNumber(orig.employeeNumber) { }

    // All STL/CLR containers require a public assignment operator.
    Employee% operator=(const Employee% orig)
    {
        if (this != %orig)
        {
            name = orig.name;
            employeeNumber = orig.employeeNumber;
        }

        return *this;
    }

    // All STL/CLR containers require a public destructor.
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

### <a name="unboxed-value-types"></a>未装箱的值类型

您还可以将未装箱的值类型插入到 STL/CLR 容器中。 未装箱的值类型是值类型尚未*装箱*到引用类型。

值类型元素可以是标准值类型之一，如 `int`，也可以是用户定义的值类型，如 `value class`。 有关详细信息，请参阅[类和结构](../extensions/classes-and-structs-cpp-component-extensions.md)

#### <a name="example"></a>示例

以下示例对第一个示例进行了修改，使 Employee 类成为一个值类型。 然后，将此值类型插入到 `cliext::set` 中，与在第一个示例中一样。

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

如果你尝试插入到容器中，值类型的句柄[编译器错误 C3225](../error-messages/compiler-errors-2/compiler-error-c3225.md)生成。

### <a name="performance-and-memory-implications"></a>性能和内存含义

在确定是否使用句柄来引用类型或值类型作为容器元素时，您必须考虑多种因素。 如果您决定使用值类型，请记住，每次将一个元素插入到容器中时，都会生成该元素的副本。 对于小对象，这应该不是问题，但是，如果插入的对象很大，则可能大大影响性能。 此外，如果使用的是值类型，则无法将一个元素同时存储在多个容器中，因为每个容器都有自己的元素副本。

如果您决定使用句柄来引用类型，则可能会改善性能，因为在容器中插入元素时无需生成元素的副本。 此外，与值类型不同的是，同一元素可以存在于多个容器中。 但是，其中如果您决定使用句柄，则必须注意确保句柄有效，且未在程序的其他地方删除它所引用的对象。

## <a name="ownership-issues-with-containers"></a>容器的所有权问题

STL/CLR 中的容器处理值语义。 每次将一个元素插入到容器中时，都会插入该元素的副本。 如果要获取类似引用的语义，则可插入指向对象的句柄，而不是对象本身。

当您调用句柄对象容器的清除或擦除方法时，不会从内存中释放句柄引用的对象。 您必须显式地删除对象，或者允许垃圾回收器在确定不再使用对象之后立即释放内存，因为这些对象驻留在托管堆上。

## <a name="see-also"></a>请参阅

[C++ 标准库参考](../standard-library/cpp-standard-library-reference.md)
