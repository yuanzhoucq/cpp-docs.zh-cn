---
title: "默认参数 | Microsoft Docs"
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
  - "参数 [C++], default"
  - "参数 [C++], 函数"
  - "声明函数, 声明符"
  - "默认参数"
  - "默认值 [C++], 参数"
  - "函数声明"
  - "函数 [C++], 默认参数"
ms.assetid: d32cf516-05cb-4d4d-b169-92f5649fdfa2
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# 默认参数
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在许多情况下，函数具有不常使用的参数，因为使用默认值便已足够。  为了解决此问题，默认参数工具允许为函数仅指定在给定调用中有意义的参数。  为了阐释此概念，请考虑[函数重载](../cpp/function-overloading.md)中所示的示例。  
  
```  
// Prototype three print functions.  
int print( char *s );                  // Print a string.  
int print( double dvalue );            // Print a double.  
int print( double dvalue, int prec );  // Print a double with a  
//  given precision.  
```  
  
 在许多应用程序中，可为 `prec` 提供合理的默认值，从而消除对两个函数的需求：  
  
```  
// Prototype two print functions.  
int print( char *s );                    // Print a string.  
int print( double dvalue, int prec=2 );  // Print a double with a  
//  given precision.  
```  
  
 略微更改了 `print` 函数的实现以反映类型 **double** 仅存在一个此类函数这一事实：  
  
```  
// default_arguments.cpp  
// compile with: /EHsc /c  
  
// Print a double in specified precision.  
//  Positive numbers for precision indicate how many digits  
//  precision after the decimal point to show. Negative  
//  numbers for precision indicate where to round the number  
//  to the left of the decimal point.  
  
#include <iostream>  
#include <math.h>  
using namespace std;  
  
int print( double dvalue, int prec ) {  
   // Use table-lookup for rounding/truncation.  
   static const double rgPow10[] = {   
      10E-7, 10E-6, 10E-5, 10E-4, 10E-3, 10E-2, 10E-1, 10E0,  
         10E1,  10E2,  10E3,  10E4, 10E5,  10E6  
   };  
   const int iPowZero = 6;  
   // If precision out of range, just print the number.  
   if( prec >= -6 && prec <= 7 )  
      // Scale, truncate, then rescale.  
      dvalue = floor( dvalue / rgPow10[iPowZero - prec] ) *  
      rgPow10[iPowZero - prec];  
   cout << dvalue << endl;  
   return cout.good();  
}  
```  
  
 若要调用新的 `print` 函数，请使用如下代码：  
  
```  
print( d );    // Precision of 2 supplied by default argument.  
print( d, 0 ); // Override default argument to achieve other  
//  results.  
```  
  
 使用默认参数时，请注意以下几点：  
  
-   默认参数仅在其中省略了尾随参数的函数调用中使用 \- 它们必须是最后的参数。  因此，以下代码是非法的：  
  
    ```  
    int print( double dvalue = 0.0, int prec );  
    ```  
  
-   默认参数不能在以后的声明中重新定义，即使重新定义的参数与原始参数相同也是如此。  因此，以下代码将生成错误：  
  
    ```  
    // Prototype for print function.  
    int print( double dvalue, int prec = 2 );  
  
    ...  
  
    // Definition for print function.  
    int print( double dvalue, int prec = 2 )  
    {  
    ...  
    }  
    ```  
  
     此代码的问题在于定义中的函数声明重新定义了 `prec` 的默认参数。  
  
-   以后的声明可添加额外的默认参数。  
  
-   可为指向函数的指针提供默认参数。  例如:  
  
    ```  
    int (*pShowIntVal)( int i = 0 );  
    ```  
  
## 请参阅  
 [C\+\+ 抽象声明符](http://msdn.microsoft.com/zh-cn/e7e18c18-0cad-4450-942b-d27e1d4dd088)