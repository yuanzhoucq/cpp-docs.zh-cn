---
title: 示例容器成员
ms.date: 11/04/2016
helpviewer_keywords:
- container classes
ms.assetid: dc5a1998-a31b-4adf-b888-8abe5b87a4e0
ms.openlocfilehash: 21d3660661e3987d1b9477bb6298373033946c06
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228110"
---
# <a name="sample-container-members"></a>示例容器成员

> [!NOTE]
> 本主题在 Microsoft c + + 文档中作为 c + + 标准库中使用的容器的非功能性示例。 有关详细信息，请参阅 [C++ 标准库容器](../standard-library/stl-containers.md)。

## <a name="reference"></a>参考

## <a name="typedefs"></a>Typedef

|||
|-|-|
|[const_iterator](../standard-library/container-class-const-iterator.md)|描述可用作受控序列常量迭代器的对象。|
|[const_reference](../standard-library/container-class-const-reference.md)|描述可用作受控序列元素的常量引用的对象。|
|[const_reverse_iterator](../standard-library/container-class-const-reverse-iterator.md)|描述可用作受控序列常量反向迭代器的对象。|
|[difference_type](../standard-library/container-class-difference-type.md)|描述可表示受控序列中任意两个元素的地址差异的对象。|
|[器](../standard-library/container-class-iterator.md)|描述可用作受控序列迭代器的对象。|
|[reference](../standard-library/container-class-reference.md)|描述可用作对受控序列元素的引用的对象。|
|[reverse_iterator](../standard-library/container-class-reverse-iterator.md)|描述可用作受控序列的反向迭代器的对象。|
|[size_type](../standard-library/container-class-size-type.md)|描述可表示任何受控序列长度的对象。|
|[value_type](../standard-library/container-class-value-type.md)|作为模板参数的同义词 `Ty` 。|

## <a name="member-functions"></a>成员函数

|||
|-|-|
|[准备](../standard-library/container-class-begin.md)|该成员函数返回一个迭代器，指向序列的第一个元素（或刚超出空序列末尾的位置）。|
|[清除](../standard-library/container-class-clear.md)|调用 [erase](../standard-library/container-class-erase.md)（[begin](../standard-library/container-class-begin.md) 和 [end](../standard-library/container-class-end.md)）。|
|[empty](../standard-library/container-class-empty.md)|返回 **`true`** 空的受控序列。|
|[end](../standard-library/container-class-end.md)|返回指向刚超出序列末尾位置的迭代器。|
|[erase](../standard-library/container-class-erase.md)|删除元素。|
|[max_size](../standard-library/container-class-max-size.md)|返回可控对象的最长序列长度，在常量时间内不考虑受控序列的长度。|
|[rbegin](../standard-library/container-class-rbegin.md)|返回指向刚超出受控序列末尾的反向迭代器并指示反向序列的开头。|
|[rend](../standard-library/container-class-rend.md)|该成员函数返回一个反向访问迭代器，其指向序列的第一个元素（或刚超出空序列末尾位置）并指示反向序列的末尾。|
|[大小](../standard-library/container-class-size.md)|返回受控序列的长度，在常量时间内不考虑受控序列的长度。|
|[swap](../standard-library/container-class-swap.md)
