---
title: '&lt;vector&gt; 函数 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vector/std::swap
ms.assetid: 6cdcf043-eef6-4330-83f0-4596fb9f968a
helpviewer_keywords:
- std::swap [vector]
ms.openlocfilehash: c93f535bb02cbaa1f688fba84f15d832381156c6
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50079307"
---
# <a name="ltvectorgt-functions"></a>&lt;vector&gt; 函数

## <a name="swap"></a>  swap

交换两个向量的元素。

```cpp
template <class Type, class Allocator>
void swap(vector<Type, Allocator>& left, vector<Type, Allocator>& right);
```

### <a name="parameters"></a>参数

*right*<br/>
提供要交换的元素的向量或其元素将要与向量的交换的向量*左*。

*left*<br/>
其元素将要与向量的交换的向量*右*。

### <a name="remarks"></a>备注

模板函数是专用于容器类矢量用以执行成员函数的算法`left`。 [vector:: swap](../standard-library/vector-class.md) *(右*)。 这些是由编译器进行的函数模板部分排序的实例。 模板函数以此种方式重载时，模板与函数调用的匹配并不唯一，随后编译器会选择此模板函数的最专用化版本。 在算法类中，模板函数的通用版本 **template** \< **class T**> **void swap**( **T&**, **T&**) 将按分配工作，是一个缓慢操作。 每个容器中的专用化版本速度快很多，因为专用化版本可适用于容器类的内部表示形式。

### <a name="example"></a>示例

有关使用 `swap` 的模板版本的示例，请参阅成员函数 [vector::swap](../standard-library/vector-class.md) 的代码示例。

## <a name="see-also"></a>请参阅

[\<vector>](../standard-library/vector.md)<br/>
