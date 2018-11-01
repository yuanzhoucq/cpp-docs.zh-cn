---
title: vector&lt;bool&gt;::reference 类
ms.date: 11/04/2016
f1_keywords:
- vector/vector<bool>::reference
helpviewer_keywords:
- vector<bool> reference class
ms.assetid: f27854f9-0ef0-4e7e-ad2e-cd53b6cb3334
ms.openlocfilehash: 7930c1cd93cd05a752d4997b9480c766ee26bd99
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50471495"
---
# <a name="vectorltboolgtreference-class"></a>vector&lt;bool&gt;::reference 类

`vector<bool>::reference` 类是 [vector\<bool> 类](../standard-library/vector-bool-class.md) 为模拟 `bool&` 而提供的一种代理类。

## <a name="remarks"></a>备注

必须使用模拟引用，因为 C++ 不允许直接引用位。 `vector<bool>` 每个元素只使用一个位，这可以使用此代理类来引用。 但是，引用模拟不会完成，原因是某些赋值无效。 例如，因为地址`vector<bool>::reference`无法创建对象，将尝试使用以下代码`vector<bool>::operator&`不正确：

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
|[operator bool](../standard-library/vector-bool-reference-operator-bool.md)|提供了隐式转换`vector<bool>::reference`到**bool**。|
|[operator=](../standard-library/vector-bool-reference-operator-assign.md)|将布尔值赋给一个位，或将引用的元素所保存的值赋给一个位。|

## <a name="requirements"></a>要求

**标头**：\<vector>

**命名空间：** std

## <a name="see-also"></a>请参阅

[\<vector>](../standard-library/vector.md)<br/>
[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[C++ 标准库参考](../standard-library/cpp-standard-library-reference.md)<br/>
