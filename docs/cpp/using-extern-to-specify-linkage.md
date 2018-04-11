---
title: "使用 extern 指定链接 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: extern
dev_langs: C++
helpviewer_keywords:
- extern keyword [C++], linkage to non-C++ functions
- declarations, external
- external linkage, extern modifier
ms.assetid: 1e2f0ae3-ae98-4410-85b5-222d6abc865a
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: db93feb8c8fad13cf8de082858e68b89f93b5323
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="using-extern-to-specify-linkage"></a>使用 extern 指定链接
## <a name="syntax"></a>语法  
  
```  
  
      extern string-literal { declaration-list }  
extern string-literal declaration  
```  
  
## <a name="remarks"></a>备注  
 `extern` 关键字声明一个变量或函数，并指定它具有外部链接（其名称在用于定义它的文件之外的其他文件中可见）。 在修改变量时，`extern` 指定该变量具有静态持续时间（在程序开始时分配，并在程序结束时释放）。 可以在另一个源文件中定义变量或函数，也可以稍后在同一个文件中进行定义。 默认情况下，文件范围内的变量和函数的声明是外部的。  
  
## <a name="example"></a>示例  
  
```  
// specifying_linkage1.cpp  
int i = 1;  
void other();  
  
int main() {  
   // Reference to i, defined above:  
   extern int i;  
}  
  
void other() {  
   // Address of global i assigned to pointer variable:  
   static int *external_i = &i;  
  
   // i will be redefined; global i no longer visible:  
   // int i = 16;  
}  
```  
  
 在 C++ 中，与字符串一起使用时，`extern` 指定其他语言的链接约定将用于声明符。 仅在之前被声明为具有 C 链接的情况下，才能访问 C 函数和数据。 但是，必须在单独编译的翻译单元中定义它们。  
  
 Microsoft C++ 支持字符串**"C"**和**"C++"**中*字符串文本*字段。 所有标准包含文件都使用 `extern` "C" 语法以允许运行库函数用于 C++ 程序。  
  
## <a name="example"></a>示例  
 以下示例演示用于声明具有 C 链接的名称的备选方法：  
  
```  
// specifying_linkage2.cpp  
// compile with: /c  
// Declare printf with C linkage.  
extern "C" int printf( const char *fmt, ... );  
  
//  Cause everything in the specified header files  
//   to have C linkage.  
extern "C" {  
   // add your #include statements here  
   #include <stdio.h>  
}  
  
//  Declare the two functions ShowChar and GetChar  
//   with C linkage.  
extern "C" {  
   char ShowChar( char ch );  
   char GetChar( void );  
}  
  
//  Define the two functions ShowChar and GetChar  
//   with C linkage.  
extern "C" char ShowChar( char ch ) {  
   putchar( ch );  
   return ch;  
}  
  
extern "C" char GetChar( void ) {  
   char ch;  
  
   ch = getchar();  
   return ch;  
}  
  
// Declare a global variable, errno, with C linkage.  
extern "C" int errno;  
```  
  
 如果函数有多个链接规范，则它们必须一致；将函数声明为同时具有 C 和 C++ 链接是错误的。 此外，如果一个函数的两个声明出现在一个程序中，并且它们一个有链接规范，另一个没有，则有链接规范的声明必须是第一个。 将为已具有链接规范的函数的所有冗余声明提供第一个声明中指定的链接。 例如:  
  
```  
extern "C" int CFunc1();  
...  
int CFunc1();            // Redeclaration is benign; C linkage is  
                         //  retained.  
  
int CFunc2();  
...  
extern "C" int CFunc2(); // Error: not the first declaration of  
                         //  CFunc2;  cannot contain linkage  
                         //  specifier.  
```  
  
 函数和对象显式声明为**静态**复合链接说明符体内 (**{}**) 将被视为静态函数或对象; 链接说明符将被忽略。 其他函数和对象的行为方式就像它们是使用 `extern` 关键字声明的一样。 (请参阅[使用 extern 指定链接](../cpp/using-extern-to-specify-linkage.md)有关的详细信息`extern`关键字。)  
  
## <a name="see-also"></a>请参阅  
 [关键字](../cpp/keywords-cpp.md)   
 [extern 存储类说明符](../c-language/extern-storage-class-specifier.md)   
 [标识符的行为](../c-language/behavior-of-identifiers.md)   
 [链接](../c-language/linkage.md)