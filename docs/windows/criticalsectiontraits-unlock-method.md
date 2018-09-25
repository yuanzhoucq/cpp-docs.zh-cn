---
title: 'Criticalsectiontraits:: Unlock 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits::Unlock
dev_langs:
- C++
helpviewer_keywords:
- Unlock method
ms.assetid: 8fb382f5-6eda-407e-9673-71d77bda4962
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5babc5c14baae474409cd364af31b70549fcefe5
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46413011"
---
# <a name="criticalsectiontraitsunlock-method"></a>CriticalSectionTraits::Unlock 方法

专门负责`CriticalSection`模板以便支持指定的关键节对象的释放所有权。

## <a name="syntax"></a>语法

```cpp
inline static void Unlock(
   _In_ Type cs
);
```

### <a name="parameters"></a>参数

*cs*<br/>
指向关键部分对象的指针。

## <a name="remarks"></a>备注

`Type`修饰符定义为`typedef CRITICAL_SECTION* Type;`。

有关详细信息，请参阅**LeaveCriticalSection 函数**中**同步函数**Windows API 文档的部分。

## <a name="requirements"></a>要求

**标头：** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers::HandleTraits

## <a name="see-also"></a>请参阅

[CriticalSectionTraits 结构](../windows/criticalsectiontraits-structure.md)