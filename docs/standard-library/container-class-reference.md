---
title: Container Class::reference | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- reference method
ms.assetid: ab85a9fb-c628-4761-9a5f-a0231fad7690
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 13883e1426be22c8cf3d329be33258c69511900d
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/11/2018
ms.locfileid: "38966007"
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
