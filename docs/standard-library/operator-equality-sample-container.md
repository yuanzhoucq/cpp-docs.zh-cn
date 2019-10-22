---
title: operator== (&lt;sample container&gt;)
ms.date: 11/04/2016
f1_keywords:
- std.==
- std::==
- operator==
- std.operator==
- std::operator==
- ==
helpviewer_keywords:
- operator ==, containers
- operator==, containers
- == operator, with specific standard C++ objects
ms.assetid: d3d8754e-5157-4b8b-bf9c-da41856f5eed
ms.openlocfilehash: 3f84e8e5f7d0c09a865fe47d7493daecf68cf60c
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689209"
---
# <a name="operator-ltsample-containergt"></a>operator== (&lt;sample container&gt;)

> [!NOTE]
> 本主题在 Microsoft C++文档中作为在C++标准库中使用的容器的非功能性示例。 有关详细信息，请参阅 [C++ 标准库容器](../standard-library/stl-containers.md)。

重载 `operator==` 比较类模板[容器](../standard-library/sample-container-class.md)的两个对象。

## <a name="syntax"></a>语法

```cpp
template <class Ty>
bool operator==(
    const Container <Ty>& left,
    const Container <Ty>& right);
```

## <a name="return-value"></a>返回值

返回 `left.`[大小](../standard-library/container-class-size.md)` == right.size && equal(left.`[开始](../standard-library/container-class-begin.md)`, left.` `, right.begin)`[结束](../standard-library/container-class-end.md)。

## <a name="see-also"></a>请参阅

[\<sample container>](../standard-library/sample-container.md)
