---
title: "this 指针 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "this"
  - "this_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "非静态成员函数"
  - "指针, 到类实例"
  - "此指针"
ms.assetid: 92e3256a-4ad9-4d46-8be1-d77fad90791f
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# this 指针
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**this** 指针是只能在 **class**、`struct`或 **union** 类型的非静态成员函数中访问的指针。  它指向为其调用成员函数的对象。  静态成员函数没有 **this** 指针。  
  
## 语法  
  
```  
  
        this   
this->member-identifier  
```  
  
## 备注  
 对象的 **this** 指针不是对象的一部分；它没有在对象上的 `sizeof` 语句的结果中反映。  相反，当对某个对象调用非静态成员函数时，该对象的地址将由编译器作为隐藏的参数传递给函数。  例如，以下函数调用：  
  
```  
myDate.setMonth( 3 );  
```  
  
 可以按以下方式解释：  
  
```  
setMonth( &myDate, 3 );  
```  
  
 对象的地址可从成员函数的内部作为 **this** 指针提供。  **this** 的大多数使用都是隐式的。  在引用类的成员时显式使用 **this** 是合法的，但没有必要。  例如:  
  
```  
void Date::setMonth( int mn )  
{  
   month = mn;            // These three statements  
   this->month = mn;      // are equivalent  
   (*this).month = mn;  
}  
```  
  
 表达式 `*this` 通常用于从成员函数返回当前对象：  
  
```  
return *this;  
```  
  
 **this** 指针还用于防止自引用：  
  
```  
if (&Object != this) {  
// do not execute in cases of self-reference  
```  
  
> [!NOTE]
>  由于 **this** 指针无法更改，因此不允许对 **this** 赋值。  C\+\+ 的早期实现允许对 **this** 赋值。  
  
 **this** 指针有时可直接使用 \- 例如，当操作自引用数据结构，而其中需要当前对象的地址时。  
  
## 示例  
  
```  
// this_pointer.cpp  
// compile with: /EHsc  
  
#include <iostream>  
#include <string.h>  
  
using namespace std;  
  
class Buf   
{  
public:  
    Buf( char* szBuffer, size_t sizeOfBuffer );  
    Buf& operator=( const Buf & );  
    void Display() { cout << buffer << endl; }  
  
private:  
    char*   buffer;  
    size_t  sizeOfBuffer;  
};  
  
Buf::Buf( char* szBuffer, size_t sizeOfBuffer )  
{  
    sizeOfBuffer++; // account for a NULL terminator  
  
    buffer = new char[ sizeOfBuffer ];  
    if (buffer)  
    {  
        strcpy_s( buffer, sizeOfBuffer, szBuffer );  
        sizeOfBuffer = sizeOfBuffer;  
    }  
}  
  
Buf& Buf::operator=( const Buf &otherbuf )   
{  
    if( &otherbuf != this )   
    {  
        if (buffer)  
            delete [] buffer;  
  
        sizeOfBuffer =  strlen( otherbuf.buffer ) + 1;   
        buffer = new char[sizeOfBuffer];  
        strcpy_s( buffer, sizeOfBuffer, otherbuf.buffer );  
    }  
    return *this;  
}  
  
int main()  
{  
    Buf myBuf( "my buffer", 10 );  
    Buf yourBuf( "your buffer", 12 );  
  
    // Display 'my buffer'  
    myBuf.Display();  
  
    // assignment opperator  
    myBuf = yourBuf;  
  
    // Display 'your buffer'  
    myBuf.Display();  
}  
```  
  
  **my buffer**  
**your buffer**   
## this 指针的类型  
 通过 **const** 和  **关键字，可以在函数声明中修改 `volatile`this** 指针的类型。  若要将函数声明为具有一个或多个关键字的特性，请将关键字添加到函数参数列表的后面。  
  
 请看以下示例：  
  
```  
// type_of_this_pointer1.cpp  
class Point  
{  
    unsigned X() const;  
};  
int main()  
{  
}  
```  
  
 上面的代码声明一个成员函数 `X`，其中，**this** 指针被视为指向 **const** 对象的 **const** 指针。  可以使用 *cv\-mod\-list* 选项的组合，但它们始终通过 **this** 修改指向的对象，而不是 **this** 指针本身。  因此，以下声明将声明函数 `X`；**this** 指针是指向 **const** 对象的 **const** 指针：  
  
```  
// type_of_this_pointer2.cpp  
class Point  
{  
    unsigned X() const;  
};  
int main()  
{  
}  
```  
  
 成员函数中 **this** 指针的类型由以下语法描述，其中，*cv\-qualifier\-list* 是从成员函数声明符中确定的，可以是 **const** 和\/或 **volatile**，而 *class\-type* 是类的名称：  
  
 *\[cv\-qualifier\-list\] class\-type*  **\* const this**  
  
 换言之，**this** 始终是 const 指针；无法重新指派它。  成员函数声明中使用的 **const** 或 `volatile` 限定符适用于由该函数范围中的 **this** 指向的类实例。  
  
 下表介绍了有关这些修饰符的工作方式的更多信息。  
  
### this 修饰符的语义  
  
|修饰符|含义|  
|---------|--------|  
|**const**|不能更改数据成员；无法调用不是 **const** 的成员函数。|  
|`volatile`|每次访问成员数据时，都会从内存中加载该数据；禁用某些优化。|  
  
 将 **const** 对象传递给不是 **const** 的成员函数是错误的。  同样，将 `volatile` 对象传递给不是 `volatile` 的成员函数也是错误的。  
  
 声明为 **const** 的成员函数不能更改数据成员 \- 在此类函数中，**this** 指针是指向 **const** 对象的指针。  
  
> [!NOTE]
>  构造函数和析构函数不能声明为 **const** 或 `volatile`。  但是，可以在 **const** 或 `volatile` 对象上调用它们。  
  
## 请参阅  
 [C\+\+ 关键字](../cpp/keywords-cpp.md)   
 [this 指针的类型](../misc/type-of-this-pointer.md)   
 [自变量匹配和 this 指针](../misc/argument-matching-and-the-this-pointer.md)