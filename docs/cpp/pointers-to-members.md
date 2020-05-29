---
title: 指向成员的指针
ms.date: 11/04/2016
helpviewer_keywords:
- declarations, pointers
- class members [C++], pointers to
- pointers, to members
- members [C++], pointers to
- pointers, declarations
ms.assetid: f42ddb79-9721-4e39-95b1-c56b55591f68
ms.openlocfilehash: adffacc3ddc08679d7db4e17e027d8a7dbe8a92b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320317"
---
# <a name="pointers-to-members"></a>指向成员的指针

指向成员的指针的声明是指针声明的特例。  它们使用以下顺序声明：

> *存储类指定程序*<sub>选择</sub> *cv 限定符*<sub>选择</sub>*类型-规范器**ms-修饰符*<sub>选择</sub>*限定名称***`::*`** *cv 限定符*<sub>选择</sub>*标识符*pm*初始化程序*<sub>选择</sub>**`;`**

1. 声明说明符：

   - 可选存储类说明符。

   - 可选**的针和****挥发**性规格。

   - 类型说明符：类型的名称。 它是要指向的成员的类型，而不是类。

1. 声明符：

   - 可选的 Microsoft 专用修饰符。 有关详细信息，请参阅特定于[Microsoft 的修饰符](../cpp/microsoft-specific-modifiers.md)。

   - 包含要指向的成员的类的限定名。

   - __`::`__ 运算符。

   - __`*`__ 运算符。

   - 可选**的针和****挥发**性规格。

   - 命名指向成员的指针的标识符。

1. 可选的指针到成员初始化器：

   - **`=`** 运算符。

   - **`&`** 运算符。

   - 类的限定名。

   - __`::`__ 运算符。

   - 相应类型的类的非静态成员的名称。

像往常一样，允许在单个声明中使用多个声明符（以及任何关联的初始值设定项）。 指向成员的指针不能指向类的静态成员、引用类型的成员或**`void`**。

指向类成员的指针与普通指针不同：它同时具有成员类型和成员所属的类的类型信息。 常规指针只标识内存中的一个对象或只具有其地址。 指向类的某个成员的指针标识类的所有实例中的该成员。 以下示例声明类、`Window` 和一些指向成员数据的指针。

```cpp
// pointers_to_members1.cpp
class Window
{
public:
   Window();                               // Default constructor.
   Window( int x1, int y1,                 // Constructor specifying
   int x2, int y2 );                       //  window size.
bool SetCaption( const char *szTitle ); // Set window caption.
   const char *GetCaption();               // Get window caption.
   char *szWinCaption;                     // Window caption.
};

// Declare a pointer to the data member szWinCaption.
char * Window::* pwCaption = &Window::szWinCaption;
int main()
{
}
```

在前面的示例中，`pwCaption`是指向 类`Window``char*`的任何类型的成员的指针。 类型 `pwCaption` 不是 `char * Window::*`。 下一个代码片段将指针声明为 `SetCaption` 和 `GetCaption` 成员函数。

```cpp
const char * (Window::*pfnwGC)() = &Window::GetCaption;
bool (Window::*pfnwSC)( const char * ) = &Window::SetCaption;
```

指针 `pfnwGC` 和 `pfnwSC` 分别指向 `GetCaption` 类的 `SetCaption` 和 `Window`。 以下代码直接使用指向成员 `pwCaption` 的指针将信息复制到窗口标题：

```cpp
Window wMainWindow;
Window *pwChildWindow = new Window;
char   *szUntitled    = "Untitled -  ";
int    cUntitledLen   = strlen( szUntitled );

strcpy_s( wMainWindow.*pwCaption, cUntitledLen, szUntitled );
(wMainWindow.*pwCaption)[cUntitledLen - 1] = '1';     //same as
//wMainWindow.SzWinCaption [cUntitledLen - 1] = '1';
strcpy_s( pwChildWindow->*pwCaption, cUntitledLen, szUntitled );
(pwChildWindow->*pwCaption)[cUntitledLen - 1] = '2'; //same as //pwChildWindow->szWinCaption[cUntitledLen - 1] = '2';
```

**`.*`** 和**`->*`** 运算符（指针到成员运算符）之间的区别是**`.*`**，运算符选择给定对象或对象引用的成员，而**`->*`** 运算符通过指针选择成员。 有关这些运算符的详细信息，请参阅[具有指针到成员运算符的表达式](../cpp/pointer-to-member-operators-dot-star-and-star.md)。

指针到成员运算符的结果是成员的类型。 在本例中，该值为 `char *`。

以下代码片段使用指向成员的指针调用成员函数 `GetCaption` 和 `SetCaption`：

```cpp
// Allocate a buffer.
enum {
    sizeOfBuffer = 100
};
char szCaptionBase[sizeOfBuffer];

// Copy the main window caption into the buffer
//  and append " [View 1]".
strcpy_s( szCaptionBase, sizeOfBuffer, (wMainWindow.*pfnwGC)() );
strcat_s( szCaptionBase, sizeOfBuffer, " [View 1]" );
// Set the child window's caption.
(pwChildWindow->*pfnwSC)( szCaptionBase );
```

## <a name="restrictions-on-pointers-to-members"></a>针对指向成员的指针的限制

静态成员的地址不是指向成员的指针。 它是指向静态成员的一个实例的常规指针。 给定类的所有对象仅存在一个静态成员的实例。 这意味着您可以使用 （**&**） 和取消引用<strong>\*</strong>运算符的普通地址。

## <a name="pointers-to-members-and-virtual-functions"></a>指向成员和虚函数的指针

通过指针到成员函数调用虚拟函数的工作方式就像该函数被直接调用一样。 在 v 表中抬起并调用了正确的函数。

一直以来，虚函数工作的关键是通过指向基类的指针来调用它们。 （有关虚拟函数的详细信息，请参阅[虚拟函数](../cpp/virtual-functions.md)。

以下代码演示如何通过指向成员函数的指针调用虚函数：

```cpp
// virtual_functions.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

class Base
{
    public:
    virtual void Print();
};
void (Base ::* bfnPrint)() = &Base :: Print;
void Base :: Print()
{
    cout << "Print function for class Base\n";
}

class Derived : public Base
{
    public:
    void Print();  // Print is still a virtual function.
};

void Derived :: Print()
{
    cout << "Print function for class Derived\n";
}

int main()
{
    Base   *bPtr;
    Base    bObject;
    Derived dObject;
    bPtr = &bObject;    // Set pointer to address of bObject.
    (bPtr->*bfnPrint)();
    bPtr = &dObject;    // Set pointer to address of dObject.
    (bPtr->*bfnPrint)();
}

//Output: Print function for class Base
Print function for class Derived
```
