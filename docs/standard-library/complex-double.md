---
title: "complex&lt;double&gt; | Microsoft Docs"
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
  - "std.complex<double>"
  - "complex<double>"
  - "std::complex<double>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "复杂 < 双 > 函数"
ms.assetid: 0d0b9d2a-9b9b-410b-82a0-86b6df127e47
caps.latest.revision: 23
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# complex&lt;double&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述一个对象，该对象存储了两个都为 **double** 类型的有序对象对*，*该有序对象对中的第一个对象表示复数的实部，第二个对象表示复数虚部。  
  
## 语法  
  
```  
template<>  
   class complex<double> {  
public:  
   constexpr complex(  
      double _RealVal = 0,   
      double _ImagVal = 0  
   );  
  
   constexpr complex(  
      const complex<double>& _ComplexNum  
   );  
   constexpr explicit complex(  
      const complex<long double>& _ComplexNum  
   );  
   // rest same as template class complex  
};  
```  
  
#### 参数  
 `_RealVal`  
 正在构造的复数实部的 **double** 类型值。  
  
 `_ImagVal`  
 正在构造的复数虚部的 **double** 类型值。  
  
 `_ComplexNum`  
 **float** 或 `long double` 类型的复数，其实部和虚部用于初始化正在构造的 **double** 类型的复数。  
  
## 返回值  
 **double** 类型的复数。  
  
## 备注  
 complex 模板类显式专用化为 **double** 类型的 complex 类仅在它所定义构造函数中与模板类不同。 从 **float** 到 **double** 类型的转换可以是隐式的，但从 `long double` 到 **double** 的转换必须是**显式的**。 使用**显式**规则可排除在最初使用赋值语法进行类型转换。  
  
 有关详细信息模板类 `complex`, ，请参阅 [complex 类](../standard-library/complex-class.md)。 有关 `complex` 模板类的成员列表，请参阅。  
  
## 示例  
  
```  
// complex_comp_dbl.cpp  
// compile with: /EHsc  
#include <complex>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   double pi = 3.14159265359;  
  
   // The first constructor specifies real & imaginary parts  
   complex <double> c1 ( 4.0 , 5.0 );  
   cout << "Specifying initial real & imaginary parts,\n"  
        << " as type double gives c1 = " << c1 << endl;  
  
   // The second constructor initializes values of the real &  
   // imaginary parts using those of complex number of type float  
   complex <float> c2float ( 4.0 , 5.0 );  
   complex <double> c2double ( c2float );  
   cout << "Implicit conversion from type float to type double,"  
        << "\n gives c2double = " << c2double << endl;  
  
   // The third constructor initializes values of the real &  
   // imaginary parts using those of a complex number  
   // of type long double  
   complex <long double> c3longdouble ( 4.0 , 5.0 );  
   complex <double> c3double ( c3longdouble );  
   cout << "Explicit conversion from type float to type double,"  
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
  
 **指定初始真实和虚数部分，如类型 double 提供 c1 \= \(4,5\) 从双精度类型，提供 c2double 的浮点类型的隐式转换 \= 从浮点类型双精度类型，提供 c3longdouble \(4,5\) 显式转换 \= \(4，5\) 个 c3 的模数恢复 c3 利用︰ abs \(c3\) \= 6.40312 从 c3 使用恢复 c3 参数︰ arg \(c3\) \= 0.896055 弧度为单位，即 51.3402 度为单位。**   
## 要求  
 **标头**：\<complex\>  
  
 **命名空间:** std  
  
## 请参阅  
 [complex 类](../standard-library/complex-class.md)   
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)