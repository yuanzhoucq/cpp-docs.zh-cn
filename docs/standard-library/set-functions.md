---
title: '&lt;set&gt; 函数'
ms.date: 11/04/2016
f1_keywords:
- set/std::swap (map)
- set/std::swap (multiset)
ms.assetid: d1277d14-8502-46c0-b820-bcda820f9406
ms.openlocfilehash: a3a63fb86caa3485b1ee14538c3eb1f1ff72923e
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2020
ms.locfileid: "78875756"
---
# <a name="ltsetgt-functions"></a>&lt;set&gt; 函数

## <a name="swap"></a>swap （map）

交换两个集的元素。

```cpp
template <class Key, class Traits, class Allocator>
void swap(set<Key, Traits, Allocator>& left, set<Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>参数

*right*\
提供要交换的元素的集，或其元素将要与集*左侧*的元素进行交换的集。

*左*\
其元素将与设置*权限*的元素进行交换的集。

### <a name="remarks"></a>备注

此模板函数是一个专用于容器类的算法，用于执行成员函数 `left.`[swap](../standard-library/set-class.md#swap)（`right`）。 这是由编译器进行的函数模板偏序实例。 模板函数以此种方式重载时，模板与函数调用的匹配并不唯一，随后编译器会选择此模板函数的最专用化版本。 模板函数的通用版本

`template` \< **classT**> **空交换**（ **t &** ， **t &** ）

在此算法中，类按赋值进行工作，这是一种慢速操作。 每个容器中的专用化版本速度快很多，因为专用化版本可适用于容器类的内部表示形式。

### <a name="example"></a>示例

有关使用 [ 模板函数的示例，请参阅成员类 ](../standard-library/set-class.md#swap)set::swap`swap` 的代码示例。

## <a name="swap_multiset"></a>交换（多重集）

交换两个多重集的元素。

```cpp
template <class Key, class Traits, class Allocator>
void swap(multiset<Key, Traits, Allocator>& left, multiset<Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>参数

*right*\
提供要交换的元素的多集，或其元素将要与所*遗留*的多重集的元素进行交换的多重集。

*左*\
其元素要与多重集*权限*的元素进行交换的多重集。

### <a name="remarks"></a>备注

此模板函数是一个专用于容器类多重集的算法，用于执行成员函数 `left.`[swap](../standard-library/multiset-class.md#swap)（`right`）。 这是由编译器进行的函数模板偏序实例。 模板函数以此种方式重载时，模板与函数调用的匹配并不唯一，随后编译器会选择此模板函数的最专用化版本。 模板函数的通用版本

`template` \< **classT**> **空交换**（ **t &** ， **t &** ）

在此算法中，类按赋值进行工作，这是一种慢速操作。 每个容器中的专用化版本速度快很多，因为专用化版本可适用于容器类的内部表示形式。

### <a name="example"></a>示例

有关使用 [ 的模板函数的示例，请参阅成员类 ](../standard-library/multiset-class.md#swap)multiset::swap`swap` 的代码示例。
