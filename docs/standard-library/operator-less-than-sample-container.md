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
ms.openlocfilehash: 57796cc69dd734ea4c619db4bd8fedbfa09ce15b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50458417"
---
# <a name="operatorlt-ltsample-containergt"></a>operator&lt; (&lt;sample container&gt;)

> [!NOTE]
> 本主题位于 Visual C++ 文档内，作为在 C++ 标准库内使用的容器的非功能性示例。 有关详细信息，请参阅 [C++ 标准库容器](../standard-library/stl-containers.md)。

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

[\<sample container>](../standard-library/sample-container.md)<br/>
[begin](../standard-library/container-class-begin.md)<br/>
[end](../standard-library/container-class-end.md)