---
title: OMP_DYNAMIC |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- OMP_DYNAMIC
dev_langs:
- C++
helpviewer_keywords:
- OMP_DYNAMIC OpenMP environment variable
ms.assetid: e306049d-b644-4b73-8b63-46c835bff98b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b02a2a4d660057ab83da39add7fd32bcff3e6d90
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46392133"
---
# <a name="ompdynamic"></a>OMP_DYNAMIC

指定 OpenMP 运行时是否可以调整并行区域中的线程数。

## <a name="syntax"></a>语法

```
set OMP_DYNAMIC[=TRUE | =FALSE]
```

## <a name="remarks"></a>备注

`OMP_DYNAMIC`环境变量可以通过重写[omp_set_dynamic](../../../parallel/openmp/reference/omp-set-dynamic.md)函数。

OpenMP 标准的 Visual c + + 实现中的默认值是`OMP_DYNAMIC=FALSE`。

有关详细信息，请参阅[4.3 OMP_DYNAMIC](../../../parallel/openmp/4-3-omp-dynamic.md)。

## <a name="example"></a>示例

下面的命令集`OMP_DYNAMIC`为 TRUE 的环境变量：

```
set OMP_DYNAMIC=TRUE
```

下面的命令显示的当前设置`OMP_DYNAMIC`环境变量：

```
set OMP_DYNAMIC
```

## <a name="see-also"></a>请参阅

[环境变量](../../../parallel/openmp/reference/openmp-environment-variables.md)