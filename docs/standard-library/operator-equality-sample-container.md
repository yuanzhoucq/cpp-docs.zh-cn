---
title: operator== (&lt;sample container&gt;) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- std.==
- std::==
- operator==
- std.operator==
- std::operator==
- ==
dev_langs:
- C++
helpviewer_keywords:
- operator ==, containers
- operator==, containers
- == operator, with specific standard C++ objects
ms.assetid: d3d8754e-5157-4b8b-bf9c-da41856f5eed
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 360c4f38b0c740d1c23b1fa9c0712eaf6657d495
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33853243"
---
# <a name="operator-ltsample-containergt"></a>operator== (&lt;sample container&gt;)

> [!NOTE]
> 本主题位于 Visual C++ 文档内，作为在 C++ 标准库内使用的容器的非功能性示例。 有关详细信息，请参阅 [C++ 标准库容器](../standard-library/stl-containers.md)。

重载 `operator==` 以比较 [Container](../standard-library/sample-container-class.md) 模板类的两个对象。

## <a name="syntax"></a>语法

```cpp
template <class Ty>
bool operator==(
    const Container <Ty>& left,
    const Container <Ty>& right);
```

## <a name="return-value"></a>返回值

返回`left.`[大小](../standard-library/container-class-size.md) ` == right.size && equal(left.`[开始](../standard-library/container-class-begin.md)`, left.`[结束](../standard-library/container-class-end.md)`, right.begin)`。

## <a name="see-also"></a>请参阅

[\<sample container>](../standard-library/sample-container.md)<br/>
