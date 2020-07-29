---
title: complex&lt;float&gt;
ms.date: 11/04/2016
f1_keywords:
- complex/std::complex<float>
helpviewer_keywords:
- complex<float> function
ms.assetid: 1178eb1e-39bd-4017-89cd-aea95f813939
ms.openlocfilehash: 441006c977b4a4249270d0f4809da0fba0163395
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230060"
---
# <a name="complexltfloatgt"></a>complex&lt;float&gt;

描述一个对象，该对象存储两个都为类型的有序对象对 **`float`** ，第一个对象表示复数的实部，第二个对象表示复数的虚部。

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
// rest same as class template complex
};
```

### <a name="parameters"></a>参数

*_RealVal*\
**`float`** 正在构造的复数的实部的类型值。

*_ImagVal*\
**`float`** 正在构造的复数虚部的类型值。

*complexNum*\
类型 **`double`** 或类型的复数， **`long double`** 其实部和虚部用于初始化正在构造的类型的复数 **`float`** 。

## <a name="return-value"></a>返回值

类型的复数 **`float`** 。

## <a name="remarks"></a>备注

类模板复杂的类模板的显式专用化只与它所 **`float`** 定义的构造函数中的类模板不同。 允许从到的转换是 **`float`** **`double`** 隐式的，但从到的到的安全转换不一定是 **`float`** **`long double`** **`explicit`** 。 使用 **`explicit`** 赋值语法将规则用于类型转换的启动。

有关类模板的详细信息 `complex` ，请参阅[complex 类](../standard-library/complex-class.md)。 有关类模板的成员列表 `complex` ，请参见。

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

**命名空间:** std

## <a name="see-also"></a>另请参阅

[complex 类](../standard-library/complex-class.md)\
[C + + 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
