---
title: '&lt;complex&gt; | Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- <complex>
- std::<complex>
dev_langs:
- C++
helpviewer_keywords:
- complex header
ms.assetid: 5e728995-3059-496a-9ce9-61d1bfbe4f2b
caps.latest.revision: 21
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 133d969121599e77e74448a0b29b4d8de56cf97d
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/26/2018
---
# <a name="ltcomplexgt"></a>&lt;complex&gt;

定义容器模板类**复杂**及其支持的模板。

## <a name="syntax"></a>语法

```cpp
#include <complex>
```

## <a name="remarks"></a>备注

一个复数是有序的实数对。 在纯粹几何术语中，复平面是真实的二维平面。 将复平面与实平面区分开来的特质在于它具有其他代数结构。 这种代数结构有两个基本操作：

- 添加定义为 (， *b*) + (*c*， *d*) = ( + *c*， *b* + *d*)

- 定义为乘法 (， *b*) \* (*c*， *d*) = (*ac*  -  *bd*， *ad* + *bc*)

带复数加法和复数乘法操作的复数集在标准代数意义上为域：

- 加法和乘法的操作是可交换且相关联的，并且乘法通过加法分配的方式与在实数域上进行的实数加法和乘法完全相同。

- 复杂的数字 （0，0） 是加法恒等元和 （1，0） 是乘法恒等元。

- 对于复数加法逆元 (， *b*) 是 (-、-*b*)，所有此类复数的乘法逆元除 （0，0） 是

   (/ (<sup>2</sup> + *b*<sup>2</sup>)、-*b*/ (<sup>2</sup> + *b*<sup>2</sup>))

通过表示复数*z* = (， *b*) 的形式*z* =   + *bi*，其中*我*<sup>2</sup> =-1，规则可以应用的实数集的代数，到的复数集和其组件。 例如：

   (1 + 2*i*) \* (2 + 3*i*)  
   = 1 \* (2 + 3*i*) + 2*i* \* (2 + 3*i*)  
   = (2 + 3*i*) + (4*i* + 6*i*<sup>2</sup>)  
   = (2 - 6) + (3 + 4)*i*  
   = -4 + 7*i*

复数的系统是一个域，但它不是一个有序域。 任何的顺序复数没有表示的字段的实际数量和及其子集，因此能应用于复数不等同性，因为它们是为实数。

表示复数 *z* 有三种常见形式：

- 笛卡尔坐标： *z* =  + *bi*

- 极坐标图： *z* = *r* (cos *p* + *我*sin *p*)

- 指数： *z* = *r* \* *e*<sup>*ip*</sup>

在复数的这些标准表示形式中使用的术语请参照如下内容：

- 笛卡尔坐标实分量或实部 *a*。

- 笛卡尔坐标虚分量或虚部 *b*。

- 模数或绝对值的数值的复数*r*。

- 自变量或相位角*p*以弧度为单位。

除非另行指定，可以返回多个值的函数所需大于-π 且小于返回其自变量的主值超过或等于 + π 以使其保持单值。 必须表示所有的角度以弧度表示，其中，在一个圆周中具有 2π 弧度 （360 度）。

### <a name="functions"></a>函数

|函数|描述|
|-|-|
|[abs](../standard-library/complex-functions.md#abs)|计算复数的模数。|
|[arg](../standard-library/complex-functions.md#arg)|从复数中提取自变量。|
|[conj](../standard-library/complex-functions.md#conj)|返回复数的复数共轭。|
|[cos](../standard-library/complex-functions.md#cos)|返回复数的余弦值。|
|[cosh](../standard-library/complex-functions.md#cosh)|返回复数的双曲余弦值。|
|[exp](../standard-library/complex-functions.md#exp)|返回复数的指数函数。|
|[imag](../standard-library/complex-functions.md#imag)|提取复数的虚分量。|
|[log](../standard-library/complex-functions.md#log)|返回复数的自然对数。|
|[log10](../standard-library/complex-functions.md#log10)|返回复数的以 10 为底的对数。|
|[norm](../standard-library/complex-functions.md#norm)|提取复数的范数。|
|[polar](../standard-library/complex-functions.md#polar)|返回以笛卡尔坐标形式表示的，对应于指定模数和自变量的复数。|
|[pow](../standard-library/complex-functions.md#pow)|计算通过进行底数为复数的另一个复数次幂运算获得的复数。|
|[real](../standard-library/complex-functions.md#real)|提取复数的实分量。|
|[sin](../standard-library/complex-functions.md#sin)|返回复数的正弦值。|
|[sinh](../standard-library/complex-functions.md#sinh)|返回复数的双曲正弦值。|
|[sqrt](../standard-library/complex-functions.md#sqrt)|返回复数的平方根。|
|[tan](../standard-library/complex-functions.md#tan)|返回复数的正切值。|
|[tanh](../standard-library/complex-functions.md#tanh)|返回复数的双曲正切值。|

### <a name="operators"></a>运算符

|运算符|描述|
|-|-|
|[operator!=](../standard-library/complex-operators.md#op_neq)|测试两个复数是否不相等，这两个复数或其中一个可能属于其类型与实部和虚部的类型相同的子集。|
|[operator*](../standard-library/complex-operators.md#op_star)|将两个复数相乘，这两个复数或其中一个可能属于其类型与实部和虚部的类型相同的子集。|
|[operator+](../standard-library/complex-operators.md#op_add)|将两个复数相加，这两个复数或其中一个可能属于其类型与实部和虚部的类型相同的子集。|
|[operator-](../standard-library/complex-operators.md#operator-)|将两个复数相减，这两个复数或其中一个可能属于其类型与实部和虚部的类型相同的子集。|
|[operator/](../standard-library/complex-operators.md#op_div)|将两个复数相除，这两个复数或其中一个可能属于其类型与实部和虚部的类型相同的子集。|
|[operator<\<](../standard-library/complex-operators.md#op_lt_lt)|一个模板函数，用于将复数插入输出流。|
|[operator==](../standard-library/complex-operators.md#op_eq_eq)|测试两个复数是否相等，这两个复数或其中一个可能属于其类型与实部和虚部的类型相同的子集。|
|[operator>>](../standard-library/complex-operators.md#op_gt_gt)|一个模板函数，用于从输入流提取复值。|

### <a name="classes"></a>类

|类|描述|
|-|-|
|[complex\<double>](../standard-library/complex-double.md)|显式专用的模板类描述一个对象，用于存储对象，这两个类型的有序的对**double**，其中第一个参数表示复数的实部，第二个表示虚数部分。|
|[complex\<float>](../standard-library/complex-float.md)|显式专用的模板类描述一个对象，用于存储对象，这两个类型的有序的对**float**，其中第一个参数表示复数的实部，第二个表示虚数部分。|
|[complex\<long double>](../standard-library/complex-long-double.md)|显式专用的模板类描述一个对象，用于存储对象，这两个类型的有序的对**长双精度**，其中第一个参数表示复数的实部，第二个表示虚数部分。|
|[complex](../standard-library/complex-class.md)|此模板类描述一个对象，该对象用于表示复数系统和执行复杂算术运算。|

### <a name="literals"></a>文本

\<complex> 标头定义以下[用户定义的文本](../cpp/user-defined-literals-cpp.md)，它创建一个实部为零、虚部为输入参数值的复数。

|||
|-|-|
|`constexpr complex<long double> operator""il(long double d)`<br /><br /> `constexpr complex<long double> operator""il(unsigned long long d)`|返回： `complex<long double>{0.0L, static_cast<long double>(d)}`|
|`constexpr complex<double> operator""i(long double d)`<br /><br /> `constexpr complex<double> operator""i(unsigned long long d)`|返回：`complex<double>{0.0, static_cast<double>(d)}`。|
|`constexpr complex<float> operator""if(long double d)`<br /><br /> `constexpr complex<float> operator""if(unsigned long long d)`|返回：`complex<float>{0.0f, static_cast<float>(d)}`。|

## <a name="see-also"></a>请参阅

[头文件引用](../standard-library/cpp-standard-library-header-files.md)<br/>
[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
