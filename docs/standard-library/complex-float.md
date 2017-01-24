---
title: "complex&lt;float&gt; | Microsoft Docs"
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
  - "std::complex<float>"
  - "std.complex<float>"
  - "complex<float>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "complex<float> 函数"
ms.assetid: 1178eb1e-39bd-4017-89cd-aea95f813939
caps.latest.revision: 23
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# complex&lt;float&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述一个对象，该对象存储两个都为 **float** 类型的有序对象对*，*该有序对象对中的第一个对象表示复数的实部，第二个对象表示复数虚部。  
  
## 语法  
  
```  
template<>  
   class complex<float> {  
public:  
   constexpr complex(  
      float _RealVal = 0,   
      float _ImagVal = 0  
   );  
  
   constexpr complex(  
      const complex<float>& _ComplexNum  
   );  
   constexpr complex(  
      const complex<double>& _ComplexNum  
   );  
   constexpr complex(  
      const complex<long double>& _ComplexNum  
   );  
   // rest same as template class complex  
};  
```  
  
#### 参数  
 `_RealVal`  
 正在构造的复数实部的 **float** 类型值。  
  
 `_ImagVal`  
 正在构造的复数虚部的 **float** 类型值。  
  
 `_ComplexNum`  
 **double** 或 `long double` 类型的复数，其实部和虚部用于初始化正在构造的 **float** 类型的复数。  
  
## 返回值  
 **float** 类型的复数。  
  
## 备注  
 模板类 complex 显式专用化为 **float** 类型的 complex 类仅在它所定义的构造函数中与模板类不同。  从 **float** 到 **double** 类型的转换可以是隐式的，但从 **float** 到 `long double` 的不太安全转换必须是**显式的**。  使用**显式**规则可排除在最初使用赋值语法进行类型转换。  
  
 有关 `complex` 模板类的详细信息，请参阅 [complex 类](../standard-library/complex-class.md)。  有关 `complex` 模板类的成员列表，请参阅。  
  
## 示例  
  
```  
// complex_comp_flt.cpp  
// compile with: /EHsc  
#include <complex>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   double pi = 3.14159265359;  
  
   // The first constructor specifies real & imaginary parts  
   complex <float> c1 ( 4.0 , 5.0 );  
   cout << "Specifying initial real & imaginary parts,\n"  
        << " as type float gives c1 = " << c1 << endl;  
  
   // The second constructor initializes values of the real &  
   // imaginary parts using those of complex number of type double  
   complex <double> c2double ( 1.0 , 3.0 );  
   complex <float> c2float ( c2double );  
   cout << "Implicit conversion from type double to type float,"  
        << "\n gives c2float = " << c2float << endl;  
  
   // The third constructor initializes values of the real &  
   // imaginary parts using those of a complex number  
   // of type long double  
   complex <long double> c3longdouble ( 3.0 , 4.0 );  
   complex <float> c3float ( c3longdouble );  
   cout << "Explicit conversion from type long double to type float,"  
        << "\n gives c3float = " << c3float << endl;  
  
   // The modulus and argument of a complex number can be recovered  
   double absc3 = abs ( c3float);  
   double argc3 = arg ( c3float);  
   cout << "The modulus of c3 is recovered from c3 using: abs ( c3 ) = "  
        << absc3 << endl;  
   cout << "Argument of c3 is recovered from c3 using:\n arg ( c3 ) = "  
        << argc3 << " radians, which is " << argc3 * 180 / pi  
        << " degrees." << endl;  
}  
```  
  
  **Specifying initial real & imaginary parts,**  
 **as type float gives c1 \= \(4,5\)**  
**Implicit conversion from type double to type float,**  
 **gives c2float \= \(1,3\)**  
**Explicit conversion from type long double to type float,**  
 **gives c3float \= \(3,4\)**  
**The modulus of c3 is recovered from c3 using: abs \( c3 \) \= 5**  
**Argument of c3 is recovered from c3 using:**  
 **arg \( c3 \) \= 0.927295 radians, which is 53.1301 degrees.**   
## 要求  
 **标头**：\<complex\>  
  
 **命名空间:** std  
  
## 请参阅  
 [complex 类](../standard-library/complex-class.md)   
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)