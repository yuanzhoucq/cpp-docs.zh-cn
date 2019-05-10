---
title: Container Class::reference
ms.date: 11/04/2016
helpviewer_keywords:
- reference method
ms.assetid: ab85a9fb-c628-4761-9a5f-a0231fad7690
ms.openlocfilehash: bd58ffafb9be65067cbff5571fe9cbf9fcd0a55d
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221592"
---
# <a name="container-classreference"></a>Container Class::reference

> [!NOTE]
> 本主题是在 microsoftC++作为容器中使用的非功能性示例文档C++标准库。 有关详细信息，请参阅 [C++ 标准库容器](../standard-library/stl-containers.md)。

描述可用作受控序列元素的引用的对象。

## <a name="syntax"></a>语法

```

typedef T2 reference;
```

## <a name="remarks"></a>备注

它被描述为未指定类型的同义词，此处`T2`(通常`Alloc::reference`)。 类型的对象`reference`可以强制转换为类型的对象[const_reference](../standard-library/container-class-const-reference.md)。

## <a name="see-also"></a>请参阅

[Sample Container 类](../standard-library/sample-container-class.md)<br/>
