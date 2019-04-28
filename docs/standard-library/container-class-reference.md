---
title: Container Class::reference
ms.date: 11/04/2016
helpviewer_keywords:
- reference method
ms.assetid: ab85a9fb-c628-4761-9a5f-a0231fad7690
ms.openlocfilehash: 4204571dba320de6248dac2cfb10ae21dc31e72c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62210934"
---
# <a name="container-classreference"></a>Container Class::reference

> [!NOTE]
> 本主题位于 Visual C++ 文档内，作为在 C++ 标准库内使用的容器的非功能性示例。 有关详细信息，请参阅 [C++ 标准库容器](../standard-library/stl-containers.md)。

描述可用作受控序列元素的引用的对象。

## <a name="syntax"></a>语法

```

typedef T2 reference;
```

## <a name="remarks"></a>备注

它被描述为未指定类型的同义词，此处`T2`(通常`Alloc::reference`)。 类型的对象`reference`可以强制转换为类型的对象[const_reference](../standard-library/container-class-const-reference.md)。

## <a name="see-also"></a>请参阅

[Sample Container 类](../standard-library/sample-container-class.md)<br/>
