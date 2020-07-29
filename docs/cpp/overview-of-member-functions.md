---
title: 成员函数概述
ms.date: 11/04/2016
helpviewer_keywords:
- this pointer, and nonstatic member functions
- nonstatic member functions [C++]
- inline functions [C++], treating member functions as
- member functions [C++], definition in class declaration
ms.assetid: 9f77a438-500e-40bb-a6c6-544678f3f4c8
ms.openlocfilehash: 81fc3ae7a732171c6bddff9f584976dd747372b4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233660"
---
# <a name="overview-of-member-functions"></a>成员函数概述

成员函数是静态或非静态的。 静态成员函数的行为与其他成员函数的行为不同，因为静态成员函数没有隐式 **`this`** 自变量。 非静态成员函数具有 **`this`** 指针。 可以在类声明的内部或外部定义成员函数（无论是静态的还是非静态的）。

如果在类声明的内部定义一个成员函数，则该函数会被视为内联函数，并且不需要用其类名来限定函数名称。 尽管在类声明中定义的函数已被视为内联函数，但您可以使用 **`inline`** 关键字来记录代码。

在类声明中声明函数的示例如下所示：

```cpp
// overview_of_member_functions1.cpp
class Account
{
public:
    // Declare the member function Deposit within the declaration
    //  of class Account.
    double Deposit( double HowMuch )
    {
        balance += HowMuch;
        return balance;
    }
private:
    double balance;
};

int main()
{
}
```

如果成员函数的定义在类声明的外部，则仅当它显式声明为时，才会将其视为内联函数 **`inline`** 。 此外，必须通过范围解析运算符 (`::`) 用类名称限定定义中的函数名称。

以下示例与类 `Account` 的以前的声明等效，只不过 `Deposit` 函数是在类声明的外部定义的：

```cpp
// overview_of_member_functions2.cpp
class Account
{
public:
    // Declare the member function Deposit but do not define it.
    double Deposit( double HowMuch );
private:
    double balance;
};

inline double Account::Deposit( double HowMuch )
{
    balance += HowMuch;
    return balance;
}

int main()
{
}
```

> [!NOTE]
> 虽然成员函数既可在类声明的内部进行定义也可单独进行定义，但在定义类后，不能将任何成员函数添加到类中。

包含成员函数的类可具有多个声明，但成员函数本身只能在程序中有一个定义。 多个定义会导致在链接时出现错误消息。 如果类包含内联函数定义，则这些函数定义必须与遵守此“一个定义”规则相同。
