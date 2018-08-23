---
title: 'Synclockwithstatust:: Islocked 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::IsLocked
dev_langs:
- C++
helpviewer_keywords:
- IsLocked method
ms.assetid: e1b75b7b-c145-471a-aa5d-71abf31f5990
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d70a2c316f9e7994292f3dc29cef5bce993778ad
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42595058"
---
# <a name="synclockwithstatustislocked-method"></a>SyncLockWithStatusT::IsLocked 方法

支持 WRL 基础结构，不应在代码中直接使用。

## <a name="syntax"></a>语法

```cpp
bool IsLocked() const;
```

## <a name="remarks"></a>备注

指示是否当前**SyncLockWithStatusT**对象拥有一个资源; 也就是，则**SyncLockWithStatusT**对象*锁定*。

## <a name="return-value"></a>返回值

**true**如果**SyncLockWithStatusT**对象是锁定; 否则为**false**。

## <a name="requirements"></a>要求

**标头：** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers::Details

## <a name="see-also"></a>请参阅

[SyncLockWithStatusT 类](../windows/synclockwithstatust-class.md)