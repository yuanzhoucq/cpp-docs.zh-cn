---
title: complex&lt;float&gt; | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- complex/std::complex<float>
dev_langs:
- C++
helpviewer_keywords:
- complex<float> function
ms.assetid: 1178eb1e-39bd-4017-89cd-aea95f813939
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 832bf638a123a24b901509d66989738f15ad44f0
ms.sourcegitcommit: 1d9bd38cacbc783fccd3884b7b92062161c91c84
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/03/2018
ms.locfileid: "48233809"
---
# <a name="complexltfloatgt"></a>complex&lt;float&gt;

描述一个对象，用于存储这两种类型的对象的有序的对**float**，则首先表示第二个复数的实部表示虚数部分。

## <a name="syntax"></a>语法

```cpp
template <>
class complex<float> {
public:
    constexpr complex(
    float _RealVal = 0,
    float _ImagVal = 0);

constexpr complex(
    const complex<float>& complexNum);

constexpr complex(
    const complex<double>& complexNum);

constexpr complex(
    const complex<long double>& complexNum);
// rest same as template class complex
};
```

### <a name="parameters"></a>参数

*_RealVal*<br/>
正在构造的复数实部的 **float** 类型值。

*_ImagVal*<br/>
正在构造的复数虚部的 **float** 类型值。

*complexNum*<br/>
类型的复数**双**类型或类型**长双精度型**其实部和虚部用于初始化类型的复数**float**正在构造。

## <a name="return-value"></a>返回值

**float** 类型的复数。

## <a name="remarks"></a>备注

模板类 complex 显式专用化为 **float** 类型的 complex 类仅在它所定义的构造函数中与模板类不同。 从转换**float**到**double**可以是隐式的但不太安全转换从**float**到**长双精度型**是将所需**显式**。 使用**显式**转换可排除使用赋值语法启动类型转换。

有关 `complex` 模板类的详细信息，请参阅 [complex 类](../standard-library/complex-class.md)。 有关 `complex` 模板类的成员列表，请参阅。

## <a name="example"></a>示例

```cpp
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
        << endl << "gives c2float = " << c2float << endl;

   // The third constructor initializes values of the real &
   // imaginary parts using those of a complex number
   // of type long double
   complex <long double> c3longdouble ( 3.0 , 4.0 );
   complex <float> c3float ( c3longdouble );
   cout << "Explicit conversion from type long double to type float,"
        << endl << "gives c3float = " << c3float << endl;

   // The modulus and argument of a complex number can be recovered
   double absc3 = abs ( c3float);
   double argc3 = arg ( c3float);
   cout << "The modulus of c3 is recovered from c3 using: abs ( c3 ) = "
        << absc3 << endl;
   cout << "Argument of c3 is recovered from c3 using:"
        << endl << "arg ( c3 ) = "
        << argc3 << " radians, which is " << argc3 * 180 / pi
        << " degrees." << endl;
}
/* Output:
Specifying initial real & imaginary parts,
as type float gives c1 = (4,5)
Implicit conversion from type double to type float,
gives c2float = (1,3)
Explicit conversion from type long double to type float,
gives c3float = (3,4)
The modulus of c3 is recovered from c3 using: abs ( c3 ) = 5
Argument of c3 is recovered from c3 using:
arg ( c3 ) = 0.927295 radians, which is 53.1301 degrees.
*/
```

## <a name="requirements"></a>要求

**标头**：\<complex>

**命名空间：** std

## <a name="see-also"></a>请参阅

[complex 类](../standard-library/complex-class.md)<br/>
[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
