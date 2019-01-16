---
title: AsyncStatusInternal 枚举
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::Details::AsyncStatusInternal
helpviewer_keywords:
- AsyncStatusInternal enumeration
ms.assetid: b783923f-3f1c-4487-9384-be572cbc62d7
ms.openlocfilehash: b38d58603eafeaa76c79873bbf375b4a3b405cdb
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/16/2019
ms.locfileid: "54335760"
---
# <a name="asyncstatusinternal-enumeration"></a>AsyncStatusInternal 枚举

支持 WRL 基础结构，不应在代码中直接使用。

## <a name="syntax"></a>语法

```cpp
enum AsyncStatusInternal;
```

## <a name="remarks"></a>备注

指定的状态的异步操作的内部枚举之间的映射和`Windows::Foundation::AsyncStatus`枚举。

## <a name="members"></a>成员

`_Created`<br/>
等效于 `::Windows::Foundation::AsyncStatus::Created`

`_Started`<br/>
等效于 `::Windows::Foundation::AsyncStatus::Started`

`_Completed`<br/>
等效于 `::Windows::Foundation::AsyncStatus::Completed`

`_Cancelled`<br/>
等效于 `::Windows::Foundation::AsyncStatus::Cancelled`

`_Error`<br/>
等效于 `::Windows::Foundation::AsyncStatus::Error`

## <a name="requirements"></a>要求

**标头：** async.h

**命名空间：** Microsoft::WRL::Details

## <a name="see-also"></a>请参阅

[Microsoft::WRL::Details 命名空间](microsoft-wrl-details-namespace.md)