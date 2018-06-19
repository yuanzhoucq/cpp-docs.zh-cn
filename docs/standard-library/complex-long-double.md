---
title: complex&lt;long double&gt; | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- std::complex<long double>
- complex<long double>
- std.complex<long double>
dev_langs:
- C++
helpviewer_keywords:
- complex<long double> function
ms.assetid: 37591991-b385-46e9-b727-d534dbc10432
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 083ef4cea345e7b600782c09a7bdfdc09b4af3d2
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
ms.locfileid: "33844668"
---
# <a name="complexltlong-doublegt"></a>complex&lt;long double&gt;

描述一个对象，该对象存储两个都为 `long double` 类型的有序对象对，该有序对中的第一个对象表示复数的实部，第二个对象表示复数虚部。

## <a name="syntax"></a>语法

```cpp
template <>
class complex<long double> {
public:
    constexpr complex(
    long double _RealVal = 0,
    long double _ImagVal = 0);

complex(
    constexpr complex<long double>& complexNum);
// rest same as template class complex
};
```

### <a name="parameters"></a>参数

`_RealVal` 类型的值**长双精度**正在构造的复数的实部。

`_ImagVal` 类型的值`long double`正在构造的复数的虚部。

`complexNum` 类型的复数**double**或类型的**float**其实部和虚部用于初始化类型的复数`long double`正在构造。

## <a name="return-value"></a>返回值

`long double` 类型的复数。

## <a name="remarks"></a>备注

模板类 complex 显式专用化为 `long double` 类型的 complex 类仅与它所定义构造函数中的模板类不同。 从 `long double` 到 **float** 类型的转换可以是隐式，但从 **double** 到 `long double` 的转换必须是**显式**的。 使用**显式**转换可排除使用赋值语法启动类型转换。

有关 `complex` 模板类的详细信息，请参阅 [complex 类](../standard-library/complex-class.md)。 有关 `complex` 模板类的成员列表，请参阅。

## <a name="example"></a>示例

```cpp
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
\* Output:
Specifying initial real & imaginary parts,
 as type float gives c1 = (4,5)
Implicit conversion from type float to type long double,
 gives c2longdouble = (1,3)
Implicit conversion from type long double to type float,
 gives c3longdouble = (3,4)
The modulus of c3 is recovered from c3 using: abs ( c3 ) = 5
Argument of c3 is recovered from c3 using:
 arg ( c3 ) = 0.927295 radians, which is 53.1301 degrees.
*\
```

## <a name="requirements"></a>要求

**标头**：\<complex>

**命名空间：** std

## <a name="see-also"></a>请参阅

[complex 类](../standard-library/complex-class.md)<br/>
[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
