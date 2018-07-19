---
title: 示例容器成员 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- container classes
ms.assetid: dc5a1998-a31b-4adf-b888-8abe5b87a4e0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 33a251b2b9bf9b010367a88a4c9f566a73acb544
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/11/2018
ms.locfileid: "38956776"
---
# <a name="sample-container-members"></a>示例容器成员

> [!NOTE]
> 本主题位于 Visual C++ 文档内，作为在 C++ 标准库内使用的容器的非功能性示例。 有关详细信息，请参阅 [C++ 标准库容器](../standard-library/stl-containers.md)。

## <a name="reference"></a>参考

## <a name="typedefs"></a>Typedef

|||
|-|-|
|[const_iterator](../standard-library/container-class-const-iterator.md)|描述可用作受控序列常量迭代器的对象。|
|[const_reference](../standard-library/container-class-const-reference.md)|描述可用作受控序列元素的常量引用的对象。|
|[const_reverse_iterator](../standard-library/container-class-const-reverse-iterator.md)|描述可用作受控序列常量反向迭代器的对象。|
|[difference_type](../standard-library/container-class-difference-type.md)|描述可表示受控序列中任意两个元素的地址差异的对象。|
|[iterator](../standard-library/container-class-iterator.md)|描述可用作受控序列迭代器的对象。|
|[reference](../standard-library/container-class-reference.md)|描述可用作对受控序列元素的引用的对象。|
|[reverse_iterator](../standard-library/container-class-reverse-iterator.md)|描述可用作受控序列反向迭代器的对象。|
|[size_type](../standard-library/container-class-size-type.md)|描述可表示任何受控序列长度的对象。|
|[value_type](../standard-library/container-class-value-type.md)|模板参数的同义词的作用`Ty`。|

## <a name="member-functions"></a>成员函数

|||
|-|-|
|[begin](../standard-library/container-class-begin.md)|该成员函数返回一个迭代器，指向序列的第一个元素（或刚超出空序列末尾的位置）。|
|[clear](../standard-library/container-class-clear.md)|调用 [erase](../standard-library/container-class-erase.md)（[begin](../standard-library/container-class-begin.md) 和 [end](../standard-library/container-class-end.md)）。|
|[empty](../standard-library/container-class-empty.md)|对于空的受控序列，该成员函数返回 **true**。|
|[end](../standard-library/container-class-end.md)|返回指向刚超出序列末尾位置的迭代器。|
|[erase](../standard-library/container-class-erase.md)|删除元素。|
|[max_size](../standard-library/container-class-max-size.md)|返回可控对象的最长序列长度，在常量时间内不考虑受控序列的长度。|
|[rbegin](../standard-library/container-class-rbegin.md)|返回指向刚超出受控序列末尾的反向迭代器并指示反向序列的开头。|
|[rend](../standard-library/container-class-rend.md)|该成员函数返回一个反向访问迭代器，其指向序列的第一个元素（或刚超出空序列末尾位置）并指示反向序列的末尾。|
|[size](../standard-library/container-class-size.md)|返回受控序列的长度，在常量时间内不考虑受控序列的长度。|
|[swap](../standard-library/container-class-swap.md)
