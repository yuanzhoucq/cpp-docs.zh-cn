---
title: 'Asyncbase:: Get_id 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::get_Id
dev_langs:
- C++
helpviewer_keywords:
- get_Id method
ms.assetid: 591d8366-ea76-4deb-9278-9d3bc394a42b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 32d2d3cd633204b44e266bddea5d16361b5e9d19
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42604445"
---
# <a name="asyncbasegetid-method"></a>AsyncBase::get_Id 方法

检索异步操作的句柄。

## <a name="syntax"></a>语法

```cpp
STDMETHOD(
   get_Id
)(unsigned int *id) override;
```

### <a name="parameters"></a>参数

*id*  
句柄所在存储的位置。

## <a name="return-value"></a>返回值

如果成功，则为 S_OK否则为 E_ILLEGAL_METHOD_CALL。

## <a name="remarks"></a>备注

此方法实现 `IAsyncInfo::get_Id`。

## <a name="requirements"></a>要求

**标头：** async.h

**命名空间：** Microsoft::WRL

## <a name="see-also"></a>请参阅

[AsyncBase 类](../windows/asyncbase-class.md)