---
title: "指向成员的指针 | Microsoft Docs"
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
  - "类成员, 指针指向"
  - "声明, 指针"
  - "成员, 指针指向"
  - "指针, 声明"
  - "指针, 到成员"
ms.assetid: f42ddb79-9721-4e39-95b1-c56b55591f68
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# 指向成员的指针
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指向成员的指针的声明是指针声明的特例。  使用以下序列来声明它们：  
  
```  
[storage-class-specifiers] [cv-qualifiers] type-specifiers [ms-modifier]  
qualified-name ::* [cv-qualifiers] identifier  
[= & qualified-name :: member-name];  
```  
  
1.  声明说明符：  
  
    -   可选存储类说明符。  
  
    -   可选 **const** 和\/或 `volatile` 说明符。  
  
    -   类型说明符：类型的名称。  这是要指向的成员的类型，而不是类。  
  
2.  声明符：  
  
    -   可选的 Microsoft 专用修饰符。  有关详细信息，请参阅 [Microsoft 专用修饰符](../cpp/microsoft-specific-modifiers.md)。  
  
    -   包含要指向的成员的类的限定名。  请参阅[名称和限定名](../misc/names-and-qualified-names.md)。  
  
    -   :: 运算符。  
  
    -   **\*** 运算符。  
  
    -   可选 **const** 和\/或 `volatile` 说明符。  
  
    -   命名指向成员的指针的标识符。  
  
    -   可选的初始值设定项：  
  
 **\=** 运算符。  
  
 **&** 运算符。  
  
 类的限定名。  
  
 `::` 运算符。  
  
 适当类型的类的非静态成员的名称。  
  
 像往常一样，允许在单个声明中使用多个声明符（以及任何关联的初始值设定项）。  
  
 指向类的成员的指针与普通指针不同，因为它有该成员的类型的类型信息和该成员所属的类的类型信息。  常规指针只标识内存中的一个对象或只具有其地址。  指向类的某个成员的指针标识类的所有实例中的该成员。  以下示例声明类、`Window` 和一些指向成员数据的指针。  
  
```  
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
  
 在前面的示例中，`pwCaption` 是一个指针，它指向具有 `Window`char\* 类型的类  **的任何成员。** 类型 `pwCaption` 不是 `char * Window::*`。  下一个代码片段将指针声明为 `SetCaption` 和 `GetCaption` 成员函数。  
  
```  
const char * (Window::*pfnwGC)() = &Window::GetCaption;  
bool (Window::*pfnwSC)( const char * ) = &Window::SetCaption;  
```  
  
 指针 `pfnwGC` 和 `pfnwSC` 分别指向 `GetCaption` 类的 `SetCaption` 和 `Window`。  以下代码直接使用指向成员 `pwCaption` 的指针将信息复制到窗口标题：  
  
```  
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
  
 **.\*** 和 **–\>\*** 运算符（指向成员的指针运算符）的区别在于 **.\*** 运算符选择成员给定的对象或对象引用，而 **–\>\*** 运算符通过指针选择成员。  （有关这些运算符的更多信息，请参阅[使用指向成员的指针运算符的表达式](../cpp/pointer-to-member-operators-dot-star-and-star.md)。）  
  
 指向成员的指针运算符的结果是成员的类型 \- 本例中为 **char \***。  
  
 以下代码片段使用指向成员的指针调用成员函数 `GetCaption` 和 `SetCaption`：  
  
```  
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
  
## 针对指向成员的指针的限制  
 静态成员的地址不是指向成员的指针。  它是指向静态成员的一个实例的常规指针。  由于给定类的所有对象只存在一个静态成员实例，因此可以使用普通的 address\-of **\(&\)** 和取消引用 **\(\*\)** 运算符。  
  
## 指向成员和虚函数的指针  
 通过指向成员函数的指针调用虚函数就如同直接调用函数一样；将在 v 表中查找并调用正确的函数。  
  
 一直以来，虚函数工作的关键是通过指向基类的指针来调用它们。  （有关虚函数的详细信息，请参阅[虚函数](../cpp/virtual-functions.md)。）  
  
 以下代码演示如何通过指向成员函数的指针调用虚函数：  
  
```  
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
  
## 请参阅  
 [C\+\+ 抽象声明符](http://msdn.microsoft.com/zh-cn/e7e18c18-0cad-4450-942b-d27e1d4dd088)