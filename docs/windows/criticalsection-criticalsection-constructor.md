---
title: 'Criticalsection:: Criticalsection 构造函数 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection::CriticalSection
dev_langs:
- C++
helpviewer_keywords:
- CriticalSection, constructor
ms.assetid: 930b89be-4d74-46bd-8879-5dd4d15bcbd0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 892a32c6ff6f8e9a3a30452d05dd6e15c38a4fa8
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42605047"
---
# <a name="criticalsectioncriticalsection-constructor"></a>CriticalSection::CriticalSection 构造函数

初始化类似 mutex 对象、但只能由单一进程的线程使用的同步对象。

## <a name="syntax"></a>语法

```cpp
explicit CriticalSection(
   ULONG spincount = 0
);
```

### <a name="parameters"></a>参数

*spincount*  
关键部分对象的旋转计数。 默认值为 0。

## <a name="remarks"></a>备注

有关关键部分和旋转计数的详细信息，请参阅`InitializeCriticalSectionAndSpinCount`函数，在**同步**部分 Windows API 文档。

## <a name="requirements"></a>要求

**标头：** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers

## <a name="see-also"></a>请参阅

[CriticalSection 类](../windows/criticalsection-class.md)