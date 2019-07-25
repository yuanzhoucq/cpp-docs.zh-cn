---
title: operator&lt; (&lt;sample container&gt;)
ms.date: 11/04/2016
f1_keywords:
- std::operator<
- operator<
- std.<
- <
- std.operator<
- std::<
helpviewer_keywords:
- < operator, comparing specific objects
- operator<, valarrays
- < operator
- operator <, valarrays
ms.assetid: 31027dd6-53be-428b-b950-1dcb25393597
ms.openlocfilehash: a286833d96e913a66240d25798e1cc230adf58b0
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458728"
---
# <a name="operatorlt-ltsample-containergt"></a>operator&lt; (&lt;sample container&gt;)

> [!NOTE]
> 本主题在 Microsoft C++文档中作为在C++标准库中使用的容器的非功能性示例。 有关详细信息，请参阅 [C++ 标准库容器](../standard-library/stl-containers.md)。

重载 **operator<** 以比较 [Container](../standard-library/sample-container-class.md) 模板类的两个对象。

## <a name="syntax"></a>语法

```cpp
template <class Ty>
bool operator<(
    const Container <Ty>& left,
    const Container <Ty>& right);
```

## <a name="return-value"></a>返回值

返回 `lexicographical_compare(left.begin, left.end, right.begin, right.end)`。

## <a name="see-also"></a>请参阅

[\<sample container>](../standard-library/sample-container.md)\
[准备](../standard-library/container-class-begin.md)\
[end](../standard-library/container-class-end.md)