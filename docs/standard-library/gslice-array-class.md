---
title: gslice_array 类
ms.date: 11/04/2016
f1_keywords:
- valarray/std::gslice_array
helpviewer_keywords:
- gslice_array class
ms.assetid: ad1b4514-b14a-4baf-a293-d5a8e8674c75
ms.openlocfilehash: 37c54d09fdfe920c832c4baa7984fee4e090d04a
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448918"
---
# <a name="gslicearray-class"></a>gslice_array 类

一个内部的辅助模板类，该类通过提供由 valarray 的泛切分定义的子集阵列之间的操作来支持泛切分对象。

## <a name="syntax"></a>语法

```cpp
template <class Type>
class gslice_array : public gsplice {
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

此类描述一个对象, 该对象存储对`va`类[valarray](../standard-library/valarray-class.md) **\<类型**的对象的引用 > 以及类[gslice](../standard-library/gslice-class.md)的`gs`对象, 该对象描述要从中进行选择的元素的序列。`valarray<Type>`对象。

只能通过编写`gslice_array<Type>`一个形式为[va&#91;gs&#93;](../standard-library/valarray-class.md#op_at)的表达式来构造对象。 类 gslice_array 的成员函数的行为类似于为定义的`valarray<Type>`对应函数签名, 只不过只影响选定元素的序列。

此模板类由某些 valarray 运算间接创建，无法直接在程序中使用。 相反，切分下标运算符使用内部辅助模板类：

`gslice_array`\<**Type**> `valarray`\<**Type**>:: `operator[]` ( **constgslice&** ).

仅通过编写`gslice_array<Type>`窗体`va[gsl]`的表达式 (对于 valarray `va`的切片`gsl` ) 构造对象。 类 gslice_array 的成员函数的行为类似于为定义的`valarray<Type>`对应函数签名, 只不过只影响选定元素的序列。 gslice_array 控制的序列由此切分构造函数的三个参数定义，即第一个切分中第一个元素的索引、每个切分中的元素数和每个切分中元素间的距离。

如下示例中：

```cpp
const size_t lv[] = {2, 3};
const size_t dv[] = {7, 2};
const valarray<size_t> len(lv, 2), str(dv, 2);

// va[gslice(3, len, str)] selects elements with
//   indices 3, 5, 7, 10, 12, 14
```

若要过程有效，索引必须有效。

## <a name="example"></a>示例

有关如何声明和使用 slice_array 的示例，请参阅 [gslice::gslice](../standard-library/gslice-class.md#gslice) 的示例。

## <a name="requirements"></a>要求

**标头：** \<valarray>

**命名空间：** std

## <a name="see-also"></a>请参阅

[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
