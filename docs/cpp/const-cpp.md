---
title: "const (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "const_cpp"
  - "const"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "const 关键字 [C++]"
ms.assetid: b21c0271-1ad0-40a0-b21c-5e812bba0318
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# const (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

修改数据声明时，**const** 关键字指定对象或变量是不可修改的。  
  
## 语法  
  
```  
  
        const declaration ;  
member-function const ;  
```  
  
## 常量值  
 **const** 关键字指定变量的值是常量并通知编译器防止程序员修改它。  
  
```  
// constant_values1.cpp  
int main() {  
   const int i = 5;  
   i = 10;   // C3892  
   i++;   // C2105  
}  
```  
  
 在 C\+\+ 中，可以使用 **const** 关键字而不是 [\#define](../preprocessor/hash-define-directive-c-cpp.md) 预处理器指令来定义常量值。  使用 **const** 定义的值需要接受类型检查，并可以替代常量表达式。  在 C\+\+ 中，可以使用 **const** 变量指定数组的大小，如下所示：  
  
```  
// constant_values2.cpp  
// compile with: /c  
const int maxarray = 255;  
char store_char[maxarray];  // allowed in C++; not allowed in C  
```  
  
 在 C 中，常量值默认为外部链接，因此它们只能出现在源文件中。  在 C\+\+ 中，常量值默认为内部链接，这使它们可以出现在标头文件中。  
  
 **const** 关键字还可在指针声明中使用。  
  
```  
// constant_values3.cpp  
int main() {  
   char *mybuf = 0, *yourbuf;  
   char *const aptr = mybuf;  
   *aptr = 'a';   // OK  
   aptr = yourbuf;   // C3892  
}  
```  
  
 指向声明为 **const** 的变量的指针只能赋给也声明为 **const** 的指针。  
  
```  
// constant_values4.cpp  
#include <stdio.h>  
int main() {  
   const char *mybuf = "test";  
   char *yourbuf = "test2";  
   printf_s("%s\n", mybuf);  
  
   const char *bptr = mybuf;   // Pointer to constant data  
   printf_s("%s\n", bptr);  
  
   // *bptr = 'a';   // Error  
}  
```  
  
 可以将指向常量数据的指针用作函数参数，以防止函数修改通过指针传递的参数。  
  
 对于声明为 **const** 的对象，只能调用[常量成员函数](../misc/constant-member-functions.md)。  这将确保从不修改常量对象。  
  
```  
birthday.getMonth();    // Okay  
birthday.setMonth( 4 ); // Error  
```  
  
 可以为非常量对象调用常量或非常量成员函数。  还可以使用 **const** 关键字重载成员函数；这使得可以对常量和非常量对象调用不同版本的函数。  
  
 不能使用 **const** 关键词声明构造函数和析构函数。  
  
## 常量成员函数  
 声明带 **const** 关键字的成员函数将指定该函数是一个“只读”函数，它不会修改为其调用该函数的对象。  常量成员函数不能修改任何非静态数据成员或调用不是常量的任何成员函数。若要声明常量成员函数，请在参数列表的右括号后放置 **const** 关键字。  声明和定义中都需要 **const** 关键字。  
  
```  
// constant_member_function.cpp  
class Date  
{  
public:  
   Date( int mn, int dy, int yr );  
   int getMonth() const;     // A read-only function  
   void setMonth( int mn );   // A write function; can't be const  
private:  
   int month;  
};  
  
int Date::getMonth() const  
{  
   return month;        // Doesn't modify anything  
}  
void Date::setMonth( int mn )  
{  
   month = mn;          // Modifies data member  
}  
int main()  
{  
   Date MyDate( 7, 4, 1998 );  
   const Date BirthDate( 1, 18, 1953 );  
   MyDate.setMonth( 4 );    // Okay  
   BirthDate.getMonth();    // Okay  
   BirthDate.setMonth( 4 ); // C2662 Error  
}  
```  
  
## C 和 C\+\+ const 的差异  
 当在 C 源代码文件中将变量声明为 **const** 时，您将通过以下方式实现：  
  
```  
const int i = 2;  
```  
  
 您随后可以在另一个模块中使用此变量，如下所示：  
  
```  
extern const int i;  
```  
  
 但若要获取与 C\+\+ 中相同的行为，则必须将 **const** 变量声明为：  
  
```  
extern const int i = 2;  
```  
  
 如果希望在 C\+\+ 源代码文件声明用于 C 源代码文件的 `extern` 变量，请使用：  
  
```  
extern "C" const int x=10;  
```  
  
 以防止 C\+\+ 编译器进行名称重整。  
  
## 备注  
 位于成员函数的参数列表之后时，**const** 关键字指定函数不会修改为其调用该函数的对象。  
  
 有关 **const** 的详细信息，请参阅下列主题：  
  
-   [常量值](../misc/constant-values.md)  
  
-   [常量成员函数](../misc/constant-member-functions.md)  
  
-   [固定和可变指针](../cpp/const-and-volatile-pointers.md)  
  
-   [类型限定符（C\# 语言参考）](../c-language/type-qualifiers.md)  
  
-   [volatile](../cpp/volatile-cpp.md)  
  
-   [\#define](../preprocessor/hash-define-directive-c-cpp.md)。  
  
## 请参阅  
 [C\+\+ 关键字](../cpp/keywords-cpp.md)