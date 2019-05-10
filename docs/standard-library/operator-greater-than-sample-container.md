---
title: operator&gt; (&lt;sample container&gt;)
ms.date: 11/04/2016
f1_keywords:
- std::operator>
- operator>
- std::>
- '>'
helpviewer_keywords:
- '> operator, comparing specific objects'
- operator >
ms.assetid: 49bd417a-3305-4ffa-9884-39d3904ed87d
ms.openlocfilehash: 6d195148e725857c16a0f037b87a7fa0f71841a4
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220483"
---
# <a name="operatorgt-ltsample-containergt"></a>operator&gt; (&lt;sample container&gt;)

> [!NOTE]
> 本主题是在 microsoftC++作为容器中使用的非功能性示例文档C++标准库。 有关详细信息，请参阅 [C++ 标准库容器](../standard-library/stl-containers.md)。

重载 **operator>** 以比较 [Container](../standard-library/sample-container-class.md) 模板类的两个对象。

## <a name="syntax"></a>语法

```cpp
template <class Ty>
bool operator*gt;(
    const Container <Ty>& left,
    const Container <Ty>& right);
```

## <a name="return-value"></a>返回值

返回 `right < left`。

## <a name="see-also"></a>请参阅

[\<sample container>](../standard-library/sample-container.md)<br/>
