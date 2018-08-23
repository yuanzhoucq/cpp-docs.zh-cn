---
title: 'Isbaseofstrict:: Value 常量 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::IsBaseOfStrict::value
dev_langs:
- C++
helpviewer_keywords:
- value constant
ms.assetid: 4a0cdab0-ba03-482b-babf-eeec519ba687
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e7159e75b03c6440dfc5742de9f98d93da47d904
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42583849"
---
# <a name="isbaseofstrictvalue-constant"></a>IsBaseOfStrict::value 常量

支持 WRL 基础结构，不应在代码中直接使用。

## <a name="syntax"></a>语法

```cpp
static const bool value = __is_base_of(Base, Derived);
```

## <a name="remarks"></a>备注

指示是否是一个类型的另一个基类。

**值**是**true**如果类型`Base`是该类型的基类`Derived`，否则它是**false**。

## <a name="requirements"></a>要求

**标头：** internal.h

**Namespace:** Microsoft::WRL::Details

## <a name="see-also"></a>请参阅

[IsBaseOfStrict 结构](../windows/isbaseofstrict-structure.md)  
[Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)