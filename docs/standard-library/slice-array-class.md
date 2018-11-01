---
title: slice_array 类
ms.date: 11/04/2016
f1_keywords:
- valarray/std::slice_array
helpviewer_keywords:
- slice_array class
ms.assetid: a182d5f7-f35c-4e76-86f2-b5ac64ddc846
ms.openlocfilehash: 9577447b2201c1c9e53192b99abad1979f45d15f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50467195"
---
# <a name="slicearray-class"></a>slice_array 类

一个内部的辅助模板类，该类通过提供由 valarray 的切分定义的子集阵列之间的操作来支持切分对象。

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

该类描述的对象将存储对 [valarray](../standard-library/valarray-class.md)**\<Type>** 对象及 [slice](../standard-library/slice-class.md) 类的对象的引用，它描述了要从 **valarray\<Type>** 对象中选择的元素序列。

此模板类由某些 valarray 运算间接创建，无法直接在程序中使用。 切分下标运算符使用的内部辅助模板类：

`slice_array`\< **Type**> `valarray`< **Type**:: `operator[]` ( `slice`).

在构造`slice_array<Type>`只通过写入形式的表达式的对象[va&#91;sl&#93;](../standard-library/valarray-class.md#op_at)，切片`sl`valarray 的`va`。 Slice_array 类的成员函数，然后就像是为定义的对应函数签名`valarray<Type>`，只不过仅所选元素的序列受到影响。 slice_array 控制的序列由构造函数的三个参数切片定义，即切片中第一个元素的索引、元素数以及元素之间的距离。 剪切自 valarray 的 slice_array`va`来声明**va**[ `slice`（2，5，3）] 选择具有索引 2、 5、 8、 11 和 14 中的元素`va`。 若要过程有效，索引必须有效。

## <a name="example"></a>示例

有关如何声明和使用 slice_array 的示例，请参阅 [slice::slice](../standard-library/slice-class.md#slice) 的示例。

## <a name="requirements"></a>要求

**标头：**\<valarray>

**命名空间：** std

## <a name="see-also"></a>请参阅

[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
