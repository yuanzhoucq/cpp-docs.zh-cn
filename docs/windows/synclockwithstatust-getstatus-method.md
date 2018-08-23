---
title: 'Synclockwithstatust:: Getstatus 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::GetStatus
dev_langs:
- C++
helpviewer_keywords:
- GetStatus method
ms.assetid: d448b51d-a63d-40d9-a9ee-4aad3204118d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c2cef491aac3350c1692c2f87236f3cbf01dd9b0
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42612073"
---
# <a name="synclockwithstatustgetstatus-method"></a>SyncLockWithStatusT::GetStatus 方法

支持 WRL 基础结构，不应在代码中直接使用。

## <a name="syntax"></a>语法

```cpp
DWORD GetStatus() const;
```

## <a name="return-value"></a>返回值

基于对象的等待操作结果**SyncLockWithStatusT**类，如[互斥体](../windows/mutex-class1.md)或[信号量](../windows/semaphore-class.md)。 零 (0) 指示等待操作返回已发出信号的状态;否则，另一种状态发生，如已用超时值。

## <a name="remarks"></a>备注

检索当前的等待状态**SyncLockWithStatusT**对象。

GetStatus() 函数用于检索基础[status_](../windows/synclockwithstatust-status-data-member.md)数据成员。 当对象基于**SyncLockWithStatusT**类执行锁定操作，该对象将会先等待对象变得可用。 这一等待操作的结果存储在`status_`数据成员。 可能值`status_`数据成员是等待操作的返回值。 有关详细信息，请参阅的返回值`WaitForSingleObjectEx()`MSDN 库中的函数。

## <a name="requirements"></a>要求

**标头：** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers::Details

## <a name="see-also"></a>请参阅

[SyncLockWithStatusT 类](../windows/synclockwithstatust-class.md)