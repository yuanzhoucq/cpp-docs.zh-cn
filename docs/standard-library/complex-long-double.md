---
title: complex&lt;long double&gt;
ms.date: 11/04/2016
f1_keywords:
- std::complex<long double>
- complex<long double>
- std.complex<long double>
helpviewer_keywords:
- complex<long double> function
ms.assetid: 37591991-b385-46e9-b727-d534dbc10432
ms.openlocfilehash: 73027ba76d608424b1a6da346e861b10c66989fe
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228383"
---
# <a name="complexltlong-doublegt"></a>complex&lt;long double&gt;

此显式专用化的类模板描述了一个对象，该对象存储两种类型的对象的有序对， **`long double`** 第一个对象表示复数的实部，第二个对象表示复数的虚部。

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

// rest same as class template complex
};
```

### <a name="parameters"></a>参数

*_RealVal*\
**`long double`** 正在构造的复数的实部的类型值。

*_ImagVal*\
**`long double`** 正在构造的复数虚部的类型值。

*complexNum*\
类型 **`double`** 或类型的复数， **`float`** 其实部和虚部用于初始化正在构造的类型的复数 **`long double`** 。

## <a name="return-value"></a>返回值

类型的复数 **`long double`** 。

## <a name="remarks"></a>备注

类模板的显式专用化 `complex` 到类型的复杂类不同于 **`long double`** 它所定义的构造函数中的类模板。 允许从到的转换是 **`long double`** **`float`** 隐式的，但从到的 **`double`** 转换 **`long double`** 是必需的 **`explicit`** 。 使用 **`explicit`** 赋值语法将规则用于类型转换的启动。

有关类模板及其成员的详细信息 `complex` ，请参阅[complex 类](../standard-library/complex-class.md)。

**特定于 Microsoft**的： **`long double`** 和 **`double`** 类型具有相同的表示形式，但它们是不同的类型。 有关详细信息，请参阅[内置类型](../cpp/fundamental-types-cpp.md)。

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
    complex<long double> c1( 4.0 , 5.0 );
    cout << "Specifying initial real & imaginary parts,\n"
        << " as type float gives c1 = " << c1 << endl;

    // The second constructor initializes values of the real &
    // imaginary parts using those of complex number of type float
    complex<float> c2float( 1.0 , 3.0 );
    complex<long double> c2longdouble ( c2float );
    cout << "Implicit conversion from type float to type long double,"
        << "\n gives c2longdouble = " << c2longdouble << endl;

    // The third constructor initializes values of the real &
    // imaginary parts using those of a complex number
    // of type double
    complex<double> c3double( 3.0 , 4.0 );
    complex<long double> c3longdouble( c3double );
    cout << "Implicit conversion from type long double to type float,"
        << "\n gives c3longdouble = " << c3longdouble << endl;

    // The modulus and argument of a complex number can be recovered
    double absc3 = abs( c3longdouble );
    double argc3 = arg( c3longdouble );
    cout << "The modulus of c3 is recovered from c3 using: abs( c3 ) = "
        << absc3 << endl;
    cout << "Argument of c3 is recovered from c3 using:\n arg( c3 ) = "
        << argc3 << " radians, which is " << argc3 * 180 / pi
        << " degrees." << endl;
}
```

```Output
Specifying initial real & imaginary parts,
as type float gives c1 = (4,5)
Implicit conversion from type float to type long double,
gives c2longdouble = (1,3)
Implicit conversion from type long double to type float,
gives c3longdouble = (3,4)
The modulus of c3 is recovered from c3 using: abs( c3 ) = 5
Argument of c3 is recovered from c3 using:
arg( c3 ) = 0.927295 radians, which is 53.1301 degrees.
```

## <a name="requirements"></a>要求

**标头**：\<complex>

**命名空间:** std

## <a name="see-also"></a>另请参阅

[complex 类](../standard-library/complex-class.md)\
[C + + 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
