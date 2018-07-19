---
title: gslice_array 类 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- valarray/std::gslice_array
dev_langs:
- C++
helpviewer_keywords:
- gslice_array class
ms.assetid: ad1b4514-b14a-4baf-a293-d5a8e8674c75
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ff44a91b4916092e319c7acc0520c49aeb9a5fa4
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/11/2018
ms.locfileid: "38953070"
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

此类描述的对象将存储对对象的引用`va`类的[valarray](../standard-library/valarray-class.md)**\<类型 >**，对象及`gs`类的[gslice](../standard-library/gslice-class.md)它描述了要从选择的元素序列`valarray<Type>`对象。

在构造`gslice_array<Type>`只通过写入形式的表达式的对象[va&#91;gs&#93;](../standard-library/valarray-class.md#op_at)。 Gslice_array 类的成员函数，然后就像是为定义的对应函数签名`valarray<Type>`，只不过仅所选元素的序列受到影响。

此模板类由某些 valarray 运算间接创建，无法直接在程序中使用。 相反，切分下标运算符使用内部辅助模板类：

`gslice_array`\<**Type**> `valarray`\<**Type**>:: `operator[]` ( **constgslice&**).

在构造`gslice_array<Type>`只通过写入形式的表达式的对象`va[gsl]`，切片`gsl`valarray 的`va`。 Gslice_array 类的成员函数，然后就像是为定义的对应函数签名`valarray<Type>`，只不过仅所选元素的序列受到影响。 gslice_array 控制的序列由此切分构造函数的三个参数定义，即第一个切分中第一个元素的索引、每个切分中的元素数和每个切分中元素间的距离。

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

**标头：**\<valarray>

**命名空间：** std

## <a name="see-also"></a>请参阅

[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
