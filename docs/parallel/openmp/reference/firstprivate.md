---
title: firstprivate |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- firstprivate
dev_langs:
- C++
helpviewer_keywords:
- firstprivate OpenMP clause
ms.assetid: db479766-6d3b-4bbd-b28e-b192d826788c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d070b8de3cf0382447c3b8e756140892dcd85edc
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46387115"
---
# <a name="firstprivate"></a>firstprivate

指定每个线程应具有它自己的实例的变量和变量应使用变量的值进行初始化，因为它在并行构造之前存在。

## <a name="syntax"></a>语法

```
firstprivate(var)
```

#### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|`var`|将初始化变量的值变量具有实例中每个线程，因为它在并行构造之前存在。 如果指定多个变量，请用逗号分隔的变量名称。|

## <a name="remarks"></a>备注

## <a name="remarks"></a>备注

`firstprivate` 适用于以下指令：

- [for](../../../parallel/openmp/reference/for-openmp.md)

- [parallel](../../../parallel/openmp/reference/parallel.md)

- [部分](../../../parallel/openmp/reference/sections-openmp.md)

- [single](../../../parallel/openmp/reference/single.md)

有关详细信息，请参阅[2.7.2.2 firstprivate](../../../parallel/openmp/2-7-2-2-firstprivate.md)。

## <a name="example"></a>示例

有关使用的示例`firstprivate`，请参阅中的示例[专用](../../../parallel/openmp/reference/private-openmp.md)。

## <a name="see-also"></a>请参阅

[子句](../../../parallel/openmp/reference/openmp-clauses.md)