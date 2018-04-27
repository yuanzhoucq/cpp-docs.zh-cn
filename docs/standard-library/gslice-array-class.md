---
title: gslice_array 类 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- valarray/std::gslice_array
dev_langs:
- C++
helpviewer_keywords:
- gslice_array class
ms.assetid: ad1b4514-b14a-4baf-a293-d5a8e8674c75
caps.latest.revision: 20
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 11fb36f16d9c9d041d25b2f5bd4be77f90533e9a
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/26/2018
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

该类描述的对象将存储对 [valarray](../standard-library/valarray-class.md)**\<Type>** 类的 **va** 对象及 [gslice](../standard-library/gslice-class.md) 类的 **gs** 对象的引用，它描述了要从 **valarray\<Type>** 对象中选择的元素序列。

只通过写入 [va&#91;gs&#93;](../standard-library/valarray-class.md#op_at) 形式的表达式即可构造 **gslice_array\<Type>** 对象。 然后 gslice_array 类的成员函数的行为方式就类似于为 **valarray\<Type>** 定义的对应的函数签名，只不过仅所选的元素的序列受到影响。

此模板类由某些 valarray 运算间接创建，无法直接在程序中使用。 相反，切分下标运算符使用内部辅助模板类：

`gslice_array`\<**Type**> `valarray`\<**Type**>:: `operator[]` ( **constgslice&**).

对于 valarray **va** 的切分 **gsl**，仅通过编写 **va[gsl]** 形式的表达式构造 **gslice_array\<Type>** 对象。 然后 gslice_array 类的成员函数的行为方式就类似于为 **valarray\<Type>** 定义的对应的函数签名，只不过仅所选的元素的序列受到影响。 gslice_array 控制的序列由此切分构造函数的三个参数定义，即第一个切分中第一个元素的索引、每个切分中的元素数和每个切分中元素间的距离。

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
