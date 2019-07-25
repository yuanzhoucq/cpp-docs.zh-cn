---
title: complex&lt;double&gt;
ms.date: 11/04/2016
f1_keywords:
- complex/std::complex<double>
helpviewer_keywords:
- complex<double> function
ms.assetid: 0d0b9d2a-9b9b-410b-82a0-86b6df127e47
ms.openlocfilehash: 565a2e6b5ee4eb495cb4cc3241bb8ce72de538a2
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68453148"
---
# <a name="complexltdoublegt"></a>complex&lt;double&gt;

描述一个对象, 该对象存储两个均为**double**类型的有序对象对, 第一个对象表示复数的实部, 第二个对象表示复数的虚部。

## <a name="syntax"></a>语法

```cpp
template <>
class complex<double> {
public:
    constexpr complex(
    double RealVal = 0,
    double ImagVal = 0);

constexpr complex(const complex<double>& complexNum);

constexpr explicit complex(const complex<long double>& complexNum);
// rest same as template class complex
};
```

### <a name="parameters"></a>参数

*RealVal*\
正在构造的复数实部的 **double** 类型值。

*ImagVal*\
正在构造的复数虚部的 **double** 类型值。

*complexNum*\
**Float**类型或**long double**类型的复数, 其实部和虚部用于初始化正在构造的**double**类型的复数。

## <a name="return-value"></a>返回值

**double** 类型的复数。

## <a name="remarks"></a>备注

complex 模板类显式专用化为 **double** 类型的 complex 类仅在它所定义的构造函数中与模板类不同。 从**float**到**double**类型的转换可以是隐式的, 但从**long double**到**double**的转换必须是**显式**的。 使用**显式**转换可排除使用赋值语法启动类型转换。

有关 `complex` 模板类的详细信息，请参阅 [complex 类](../standard-library/complex-class.md)。 有关 `complex` 模板类的成员列表，请参阅。

## <a name="example"></a>示例

```cpp
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
        << "as type double gives c1 = " << c1 << endl;

   // The second constructor initializes values of the real &
   // imaginary parts using those of complex number of type float
   complex <float> c2float ( 4.0 , 5.0 );
   complex <double> c2double ( c2float );
   cout << "Implicit conversion from type float to type double,"
        << endl << "gives c2double = " << c2double << endl;

   // The third constructor initializes values of the real &
   // imaginary parts using those of a complex number
   // of type long double
   complex <long double> c3longdouble ( 4.0 , 5.0 );
   complex <double> c3double ( c3longdouble );
   cout << "Explicit conversion from type float to type double,"
        << endl << "gives c3longdouble = " << c3longdouble << endl;

   // The modulus and argument of a complex number can be recovered
   double absc3 = abs ( c3longdouble );
   double argc3 = arg ( c3longdouble );
   cout << "The modulus of c3 is recovered from c3 using: abs ( c3 ) = "
        << absc3 << endl;
   cout << "Argument of c3 is recovered from c3 using:" << endl
        << "arg ( c3 ) = " << argc3 << " radians, which is "
        << argc3 * 180 / pi << " degrees." << endl;
}
/* Output:
Specifying initial real & imaginary parts,
as type double gives c1 = (4,5)
Implicit conversion from type float to type double,
gives c2double = (4,5)
Explicit conversion from type float to type double,
gives c3longdouble = (4,5)
The modulus of c3 is recovered from c3 using: abs ( c3 ) = 6.40312
Argument of c3 is recovered from c3 using:
arg ( c3 ) = 0.896055 radians, which is 51.3402 degrees.
*/
```

## <a name="requirements"></a>要求

**标头**：\<complex>

**命名空间：** std

## <a name="see-also"></a>请参阅

[complex 类](../standard-library/complex-class.md)\
[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
