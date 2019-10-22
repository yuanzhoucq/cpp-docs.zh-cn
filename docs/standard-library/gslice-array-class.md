---
title: gslice_array 类
ms.date: 11/04/2016
f1_keywords:
- valarray/std::gslice_array
helpviewer_keywords:
- gslice_array class
ms.assetid: ad1b4514-b14a-4baf-a293-d5a8e8674c75
ms.openlocfilehash: 68ce774128395e941ff80580a02c4ee28a74a4e4
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689601"
---
# <a name="gslice_array-class"></a>gslice_array 类

一个内部的辅助类模板，它通过提供由 valarray 的常规切片定义的子集数组之间的操作来支持常规切片对象。

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

此类描述一个对象，该对象存储对类[valarray](../standard-library/valarray-class.md)  **\<Type >** 的对象 `va` 的引用以及类[gslice](../standard-library/gslice-class.md)的对象 `gs`，该类描述要从 `valarray<Type>` 对象中选择的元素的序列。

仅通过编写一个形式为[va&#91;gs&#93;](../standard-library/valarray-class.md#op_at)的表达式来构造一个 `gslice_array<Type>` 对象。 类 gslice_array 的成员函数的行为类似于为 `valarray<Type>` 定义的相应函数签名，只不过只影响选定元素的序列。

类模板由某些 valarray 操作间接创建，无法在程序中直接使用。 切片下标运算符改用内部辅助类模板：

`gslice_array`\<**Type**> `valarray`\<**Type**>:: `operator[]` ( **constgslice&** ).

您只能通过为 valarray `va` 的切片 `gsl` 编写 `va[gsl]` 格式的表达式来构造一个 `gslice_array<Type>` 对象。 类 gslice_array 的成员函数的行为类似于为 `valarray<Type>` 定义的相应函数签名，只不过只影响选定元素的序列。 gslice_array 控制的序列由此切分构造函数的三个参数定义，即第一个切分中第一个元素的索引、每个切分中的元素数和每个切分中元素间的距离。

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

**命名空间:** std

## <a name="see-also"></a>请参阅

[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
