---
title: 'Synclockt:: Islocked 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT::IsLocked
dev_langs:
- C++
helpviewer_keywords:
- IsLocked method
ms.assetid: a81fea43-f99a-4708-812a-7fd6af500d3d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ca4391539e4f6987431e8b9b036053db02218007
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42593050"
---
# <a name="synclocktislocked-method"></a>SyncLockT::IsLocked 方法

支持 WRL 基础结构，不应在代码中直接使用。

## <a name="syntax"></a>语法

```cpp
bool IsLocked() const;
```

## <a name="return-value"></a>返回值

**true**如果**SyncLockT**对象是锁定; 否则为**false**。

## <a name="remarks"></a>备注

指示是否当前**SyncLockT**对象拥有一个资源; 也就是，则**SyncLockT**对象*锁定*。

## <a name="requirements"></a>要求

**标头：** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers::Details

## <a name="see-also"></a>请参阅

[SyncLockT 类](../windows/synclockt-class.md)