---
title: slice_array 类
ms.date: 11/04/2016
f1_keywords:
- valarray/std::slice_array
helpviewer_keywords:
- slice_array class
ms.assetid: a182d5f7-f35c-4e76-86f2-b5ac64ddc846
ms.openlocfilehash: 358348a57b823fcea82cd296967c83778819361d
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688960"
---
# <a name="slice_array-class"></a>slice_array 类

一个内部的辅助类模板，它通过提供由 valarray 的切片定义的子集数组之间的操作来支持切片对象。

## <a name="syntax"></a>语法

```cpp
template <class Type>
class slice_array : public slice {
public:
    typedef Type value_type;
    void operator=(const valarray<Type>& x) const;
    void operator=(const Type& x) const;
    void operator*=(const valarray<Type>& x) const;
    void operator/=(const valarray<Type>& x) const;
    void operator%=(const valarray<Type>& x) const;
    void operator+=(const valarray<Type>& x) const;
    void operator-=(const valarray<Type>& x) const;
    void operator^=(const valarray<Type>& x) const;
    void operator&=(const valarray<Type>& x) const;
    void operator|=(const valarray<Type>& x) const;
    void operator<<=(const valarray<Type>& x) const;
    void operator>>=(const valarray<Type>& x) const;
    // The rest is private or implementation defined
}
```

## <a name="remarks"></a>备注

该类描述的对象将存储对 [valarray](../standard-library/valarray-class.md) **\<Type>** 对象及 [slice](../standard-library/slice-class.md) 类的对象的引用，它描述了要从 **valarray\<Type>** 对象中选择的元素序列。

类模板由某些 valarray 操作间接创建，无法在程序中直接使用。 切片下标运算符使用的内部辅助类模板：

`slice_array`\< **Type**> `valarray`< **Type**:: `operator[]` ( `slice`).

只需要编写一个形式为[va&#91;sl&#93;](../standard-library/valarray-class.md#op_at)的表达式（对于 valarray `va` 的切片 `sl` 构造 `slice_array<Type>` 对象）。 类 slice_array 的成员函数的行为类似于为 `valarray<Type>` 定义的相应函数签名，只不过只影响选定元素的序列。 slice_array 控制的序列由构造函数的三个参数切片定义，即切片中第一个元素的索引、元素数以及元素之间的距离。 **Va**[`slice` （2，5，3）] 声明的 valarray `va` 的 slice_array 剪切从 `va` 中选择索引为2、5、8、11和14的元素。 若要过程有效，索引必须有效。

## <a name="example"></a>示例

有关如何声明和使用 slice_array 的示例，请参阅 [slice::slice](../standard-library/slice-class.md#slice) 的示例。

## <a name="requirements"></a>要求

**标头：** \<valarray>

**命名空间:** std

## <a name="see-also"></a>请参阅

[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
