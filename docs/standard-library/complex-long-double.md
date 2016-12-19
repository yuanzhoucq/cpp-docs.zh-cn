---
title: "complex&lt;long double&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::complex<long double>"
  - "complex<long double>"
  - "std.complex<long double>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "complex<long double> 函数"
ms.assetid: 37591991-b385-46e9-b727-d534dbc10432
caps.latest.revision: 20
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# complex&lt;long double&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述一个对象，该对象存储两个都为 `long double` 类型的有序对象对，该有序对中的第一个对象表示复数的实部，第二个对象表示复数虚部。  
  
## 语法  
  
```  
template<>  
   class complex<long double> {  
public:  
   constexpr complex(  
      long double _RealVal = 0,   
      long double _ImagVal = 0  
   );  
complex(  
      constexpr complex<long double>& _ComplexNum  
   );  
   // rest same as template class complex  
};  
```  
  
#### 参数  
 `_RealVal`  
 正在构造的复数实部的 **long double** 类型值。  
  
 `_ImagVal`  
 正在构造的复数虚部的 `long double` 类型值。  
  
 `_ComplexNum`  
 类型为 **double** 或 **float** 的复数，其实部和虚部用于初始化正在构造的 `long double` 类型的复数。  
  
## 返回值  
 `long double` 类型的复数。  
  
## 备注  
 模板类 complex 显式专用化为 `long double` 类型的 complex 类仅与它所定义构造函数中的模板类不同。  从 `long double` 到 **float** 类型的转换可以是隐式，但从 **double** 到 `long double` 的转换必须是**显式**的。  使用**显式**转换可排除在最初使用赋值语法进行类型转换。  
  
 有关模板类 `complex` 的详细信息，请参阅 [complex 类](../standard-library/complex-class.md)。  有关模板类 `complex` 的成员列表，请参阅。  
  
## 示例  
  
```  
// complex_comp_ld.cpp  
// compile with: /EHsc  
#include <complex>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   double pi = 3.14159265359;  
  
   // The first constructor specifies real & imaginary parts  
   complex <long double> c1 ( 4.0 , 5.0 );  
   cout << "Specifying initial real & imaginary parts,\n"  
        << " as type float gives c1 = " << c1 << endl;  
  
   // The second constructor initializes values of the real &  
   // imaginary parts using those of complex number of type float  
   complex <float> c2float ( 1.0 , 3.0 );  
   complex <long double> c2longdouble ( c2float );  
   cout << "Implicit conversion from type float to type long double,"  
        << "\n gives c2longdouble = " << c2longdouble << endl;  
  
   // The third constructor initializes values of the real &  
   // imaginary parts using those of a complex number  
   // of type double  
   complex <double> c3double ( 3.0 , 4.0 );  
   complex <long double> c3longdouble ( c3double );  
   cout << "Implicit conversion from type long double to type float,"  
        << "\n gives c3longdouble = " << c3longdouble << endl;  
  
   // The modulus and argument of a complex number can be recovered  
   double absc3 = abs ( c3longdouble );  
   double argc3 = arg ( c3longdouble );  
   cout << "The modulus of c3 is recovered from c3 using: abs ( c3 ) = "  
        << absc3 << endl;  
   cout << "Argument of c3 is recovered from c3 using:\n arg ( c3 ) = "  
        << argc3 << " radians, which is " << argc3 * 180 / pi  
        << " degrees." << endl;  
}  
```  
  
  **指定初始实部和虚部，**  
 **当 float 类型给定 c1 \= \(4,5\) 时**  
**从 float 类型隐式转换为 long double 类型，**  
 **当给定 c2longdouble \= \(1,3\) 时**  
**从 long double 类型隐式转换为 float 类型，**  
 **当给定 c3longdouble \= \(3,4\) 时**  
**c3 模块已使用 abs \( c3 \) \= 5 从 c3 恢复**  
**c3 变量已使用以下值从 c3 恢复：**  
 **arg \( c3 \) \= 0.927295 弧度，即 53.1301 度。**   
## 要求  
 **标头**：\<complex\>  
  
 **命名空间:** std  
  
## 请参阅  
 [complex 类](../standard-library/complex-class.md)   
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)