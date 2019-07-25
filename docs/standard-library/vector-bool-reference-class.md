---
title: vector&lt;bool&gt;::reference 类
ms.date: 11/04/2016
f1_keywords:
- vector/vector<bool>::reference
helpviewer_keywords:
- vector<bool> reference class
ms.assetid: f27854f9-0ef0-4e7e-ad2e-cd53b6cb3334
ms.openlocfilehash: 65bfc91cf5dc79fb1e5151a6f62c394b4579883b
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68453212"
---
# <a name="vectorltboolgtreference-class"></a>vector&lt;bool&gt;::reference 类

`vector<bool>::reference` 类是 [vector\<bool> 类](../standard-library/vector-bool-class.md) 为模拟 `bool&` 而提供的一种代理类。

## <a name="remarks"></a>备注

必须使用模拟引用，因为 C++ 不允许直接引用位。 `vector<bool>` 每个元素只使用一个位，这可以使用此代理类来引用。 但是，引用模拟不会完成，原因是某些赋值无效。 例如, 由于无法采用`vector<bool>::reference`对象的地址, 因此以下尝试使用`vector<bool>::operator&`的代码不正确:

```cpp
vector<bool> vb;
// ...
bool* pb = &vb[1]; // conversion error - do not use
bool& refb = vb[1];   // conversion error - do not use
```

### <a name="member-functions"></a>成员函数

|成员函数|描述|
|-|-|
|[flip](../standard-library/vector-bool-reference-flip.md)|反转向量元素的布尔值。|
|[operator bool](../standard-library/vector-bool-reference-operator-bool.md)|提供从`vector<bool>::reference`到**bool**的隐式转换。|
|[operator=](../standard-library/vector-bool-reference-operator-assign.md)|将布尔值赋给一个位，或将引用的元素所保存的值赋给一个位。|

## <a name="requirements"></a>要求

**标头**：\<vector>

**命名空间：** std

## <a name="see-also"></a>请参阅

[\<vector>](../standard-library/vector.md)\
[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C++ 标准库参考](../standard-library/cpp-standard-library-reference.md)
