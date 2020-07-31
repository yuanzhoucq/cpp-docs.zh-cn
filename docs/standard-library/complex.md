---
title: '&lt;complex&gt;'
ms.date: 11/04/2016
f1_keywords:
- <complex>
- std::<complex>
helpviewer_keywords:
- complex header
ms.assetid: 5e728995-3059-496a-9ce9-61d1bfbe4f2b
ms.openlocfilehash: 2c6487370bfa4d3af6c9c7c40b7f83a252c2e01d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222571"
---
# <a name="ltcomplexgt"></a>&lt;complex&gt;

定义容器类模板 `complex` 及其支持的模板。

## <a name="requirements"></a>要求

**标头**：\<complex>

**命名空间:** std

## <a name="remarks"></a>备注

一个复数是有序的实数对。 在纯粹几何术语中，复平面是真实的二维平面。 将复平面与实平面区分开来的特质在于它具有其他代数结构。 这种代数结构有两个基本操作：

- 加法定义为（*a*， *b*） + （*c*， *d*） = （*a*  +  *c*， *b*  +  *d*）

- 乘法定义为（*a*， *b*） \* （*c*， *d*） = （*ac*  -  *bd*， *ad*  +  *bc*）

带复数加法和复数乘法操作的复数集在标准代数意义上为域：

- 加法和乘法的操作是可交换且相关联的，并且乘法通过加法分配的方式与在实数域上进行的实数加法和乘法完全相同。

- 复数 (0, 0) 是加法恒等元，(1, 0) 是乘法恒等元。

- 复数（*a*， *b*）的加法逆元是（-*a*，-*b*），除（0，0）外的所有此类复数的乘法倒数是

   （*a*/（*a*<sup>2</sup>  +  *b*<sup>2</sup>），-*b*/（*a*<sup>2</sup>  +  *b*<sup>2</sup>））

通过以*z*a bi 形式表示一个复数*z* = （*a*， *b*）  =  *a*  +  *bi*，其中*i*<sup>2</sup> =-1，实数集的代数规则可应用于一组复数及其组件。 例如：

   （1 + 2*i*） \*（2 + 3*i*） = 1 \* （2 + 3*i*） + 2*i* \* （2 + 3*i*） = （2 + 3*i*） + （4*i* + 6*i*<sup>2</sup>） = （2-6） + （3 + 4）*i* =-4 + 7*i*

复数的系统是一个域，但它不是一个有序域。 对于实数及其子集的字段，不能进行复数排序，因此不相等不能应用于复数，因为它是实际数字。

表示复数 *z* 有三种常见形式：

- 笛卡尔： *z*  =  *a*  +  *bi*

- 极坐标： *z*  =  *r* （cos *p*  +  *i* sin *p*）

- 指数： *z*  =  *r* \* *e*<sup>*ip*</sup>

在复数的这些标准表示形式中使用的术语请参照如下内容：

- 笛卡尔坐标实分量或实部 *a*。

- 笛卡尔坐标虚分量或虚部 *b*。

- 复数*r*的模数或绝对值。

- 参数或相位角度*p* （以弧度表示）。

除非另外指定，否则，可以返回多个值的函数需要返回大于-π且小于或等于 + π的参数的主体值，以使其保持单值。 所有角度必须以弧度表示，其中有2π弧度（360度）。

## <a name="members"></a>成员

### <a name="functions"></a>函数

|||
|-|-|
|[abs](../standard-library/complex-functions.md#abs)|计算复数的模数。|
|[acos](../standard-library/complex-functions.md#acos)||
|[acosh](../standard-library/complex-functions.md#acosh)||
|[与我们联系](../standard-library/complex-functions.md#arg)|从复数中提取自变量。|
|[asin](../standard-library/complex-functions.md#asin)||
|[asinh](../standard-library/complex-functions.md#asinh)||
|[atan](../standard-library/complex-functions.md#atan)||
|[atanh](../standard-library/complex-functions.md#atanh)||
|[conj](../standard-library/complex-functions.md#conj)|返回复数的复数共轭。|
|[缆](../standard-library/complex-functions.md#cos)|返回复数的余弦值。|
|[cosh](../standard-library/complex-functions.md#cosh)|返回复数的双曲余弦值。|
|[exp](../standard-library/complex-functions.md#exp)|返回复数的指数函数。|
|[imag](../standard-library/complex-functions.md#imag)|提取复数的虚分量。|
|[日志](../standard-library/complex-functions.md#log)|返回复数的自然对数。|
|[log10](../standard-library/complex-functions.md#log10)|返回复数的以 10 为底的对数。|
|[norm](../standard-library/complex-functions.md#norm)|提取复数的范数。|
|[polar](../standard-library/complex-functions.md#polar)|返回以笛卡尔坐标形式表示的，对应于指定模数和自变量的复数。|
|[pow](../standard-library/complex-functions.md#pow)|计算通过进行底数为复数的另一个复数次幂运算获得的复数。|
|[proj](../standard-library/complex-functions.md#proj)||
|[real](../standard-library/complex-functions.md#real)|提取复数的实分量。|
|[sin](../standard-library/complex-functions.md#sin)|返回复数的正弦值。|
|[sinh](../standard-library/complex-functions.md#sinh)|返回复数的双曲正弦值。|
|[sqrt](../standard-library/complex-functions.md#sqrt)|返回复数的平方根。|
|[tan](../standard-library/complex-functions.md#tan)|返回复数的正切值。|
|[tanh](../standard-library/complex-functions.md#tanh)|返回复数的双曲正切值。|

### <a name="operators"></a>运算符

|||
|-|-|
|[operator！ =](../standard-library/complex-operators.md#op_neq)|测试两个复数是否不相等，这两个复数或其中一个可能属于其类型与实部和虚部的类型相同的子集。|
|[操作员](../standard-library/complex-operators.md#op_star)|将两个复数相乘，这两个复数或其中一个可能属于其类型与实部和虚部的类型相同的子集。|
|[operator +](../standard-library/complex-operators.md#op_add)|将两个复数相加，这两个复数或其中一个可能属于其类型与实部和虚部的类型相同的子集。|
|[操作员](../standard-library/complex-operators.md#operator-)|将两个复数相减，这两个复数或其中一个可能属于其类型与实部和虚部的类型相同的子集。|
|[操作员](../standard-library/complex-operators.md#op_div)|将两个复数相除，这两个复数或其中一个可能属于其类型与实部和虚部的类型相同的子集。|
|[运算符<\<](../standard-library/complex-operators.md#op_lt_lt)|一个模板函数，用于将复数插入输出流。|
|[operator = =](../standard-library/complex-operators.md#op_eq_eq)|测试两个复数是否相等，这两个复数或其中一个可能属于其类型与实部和虚部的类型相同的子集。|
|[运算符>>](../standard-library/complex-operators.md#op_gt_gt)|一个模板函数，用于从输入流提取复值。|

### <a name="classes"></a>类

|||
|-|-|
|[过于\<double>](../standard-library/complex-double.md)|显式专用化的类模板描述了一个对象，该对象存储两个都为类型的有序对象对， **`double`** 其中第一个对象表示复数的实部，第二个对象表示虚部。|
|[过于\<float>](../standard-library/complex-float.md)|显式专用化的类模板描述了一个对象，该对象存储两个都为类型的有序对象对， **`float`** 其中第一个对象表示复数的实部，第二个对象表示虚部。|
|[过于\<long double>](../standard-library/complex-long-double.md)|显式专用化的类模板描述了一个对象，该对象存储两个都为类型的有序对象对， **`long double`** 其中第一个对象表示复数的实部，第二个对象表示虚部。|
|[过于](../standard-library/complex-class.md)|类模板描述了一个对象，该对象用于表示复数系统和执行复杂算术运算。|

### <a name="literals"></a>文字

\<complex>标头定义了以下[用户定义的文本](../cpp/user-defined-literals-cpp.md)，这些文本创建了实部为零的复数，虚部为输入参数的值。

|||
|-|-|
|`constexpr complex<long double> operator""il(long double d)`<br />`constexpr complex<long double> operator""il(unsigned long long d)`|返回：`complex<long double>{0.0L, static_cast<long double>(d)}`|
|`constexpr complex<double> operator""i(long double d)`<br />`constexpr complex<double> operator""i(unsigned long long d)`|返回：`complex<double>{0.0, static_cast<double>(d)}`。|
|`constexpr complex<float> operator""if(long double d)`<br />`constexpr complex<float> operator""if(unsigned long long d)`|返回：`complex<float>{0.0f, static_cast<float>(d)}`。|

## <a name="see-also"></a>另请参阅

[标头文件引用](../standard-library/cpp-standard-library-header-files.md)\
[C + + 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
