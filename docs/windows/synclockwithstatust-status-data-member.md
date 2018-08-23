---
title: 'Synclockwithstatust:: Status_ 数据成员 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::status_
dev_langs:
- C++
helpviewer_keywords:
- status_ data member
ms.assetid: 466fa336-b5ff-4d43-8efd-1e87e5fddf88
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d4a9a65e7ba45d38084d1695932c3897de583f49
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42610022"
---
# <a name="synclockwithstatuststatus-data-member"></a>SyncLockWithStatusT::status_ 数据成员

支持 WRL 基础结构，不应在代码中直接使用。

## <a name="syntax"></a>语法

```cpp
DWORD status_;
```

## <a name="remarks"></a>备注

保存后对象的锁操作取决于当前的基础的等待操作结果**SyncLockWithStatusT**对象。

## <a name="requirements"></a>要求

**标头：** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers::Details

## <a name="see-also"></a>请参阅

[SyncLockWithStatusT 类](../windows/synclockwithstatust-class.md)