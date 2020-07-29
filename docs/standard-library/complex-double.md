---
title: complex&lt;double&gt;
ms.date: 11/04/2016
f1_keywords:
- complex/std::complex<double>
helpviewer_keywords:
- complex<double> function
ms.assetid: 0d0b9d2a-9b9b-410b-82a0-86b6df127e47
ms.openlocfilehash: b9bf4780dd78800653804762301b36ff6bb30a92
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230073"
---
# <a name="complexltdoublegt"></a>complex&lt;double&gt;

描述一个对象，该对象存储两个都为类型的有序对象对 **`double`** ，第一个对象表示复数的实部，第二个对象表示复数的虚部。

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
// rest same as class template complex
};
```

### <a name="parameters"></a>参数

*RealVal*\
**`double`** 正在构造的复数的实部的类型值。

*ImagVal*\
**`double`** 正在构造的复数虚部的类型值。

*complexNum*\
类型 **`float`** 或类型的复数， **`long double`** 其实部和虚部用于初始化正在构造的类型的复数 **`double`** 。

## <a name="return-value"></a>返回值

类型的复数 **`double`** 。

## <a name="remarks"></a>备注

类模板复杂的类模板的显式专用化只与它所 **`double`** 定义的构造函数中的类模板不同。 允许从到的转换是 **`float`** **`double`** 隐式的，但从到的 **`long double`** 转换 **`double`** 是必需的 **`explicit`** 。 使用 **`explicit`** 赋值语法将规则用于类型转换的启动。

有关类模板的详细信息 `complex` ，请参阅[complex 类](../standard-library/complex-class.md)。 有关类模板的成员列表 `complex` ，请参见。

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

**命名空间:** std

## <a name="see-also"></a>另请参阅

[complex 类](../standard-library/complex-class.md)\
[C + + 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
