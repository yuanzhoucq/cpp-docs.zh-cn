---
title: 'Asyncbase:: Currentstatus 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::CurrentStatus
dev_langs:
- C++
helpviewer_keywords:
- CurrentStatus method
ms.assetid: 26ee4c4a-6525-4a5f-b49c-3ca40c365eb6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 193f4d26f7e163707092f3d0bc8f981a02611a22
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42603697"
---
# <a name="asyncbasecurrentstatus-method"></a>AsyncBase::CurrentStatus 方法

检索当前的异步操作的状态。

## <a name="syntax"></a>语法

```cpp
inline void CurrentStatus(
   Details::AsyncStatusInternal *status
);
```

### <a name="parameters"></a>参数

*status*  
此操作存储的当前状态的位置。

## <a name="remarks"></a>备注

此操作是线程安全的。

## <a name="requirements"></a>要求

**标头：** async.h

**命名空间：** Microsoft::WRL

## <a name="see-also"></a>请参阅

[AsyncBase 类](../windows/asyncbase-class.md)  
[AsyncStatusInternal 枚举](../windows/asyncstatusinternal-enumeration.md)