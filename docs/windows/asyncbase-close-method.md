---
title: 'Asyncbase:: Close 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::Close
dev_langs:
- C++
helpviewer_keywords:
- Close method
ms.assetid: a52b1124-754b-4393-b491-64aae0c22f1c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 732eb6f8668f7742e23e1ea410dcc659bc3d36c7
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42605341"
---
# <a name="asyncbaseclose-method"></a>AsyncBase::Close 方法

关闭的异步操作。

## <a name="syntax"></a>语法

```cpp
STDMETHOD(
   Close
)(void) override;
```

## <a name="return-value"></a>返回值

如果该操作将关闭，或者已经为 S_OK 关闭;否则为 E_ILLEGAL_STATE_CHANGE。

## <a name="remarks"></a>备注

**Close （)** 是默认实现`IAsyncInfo::Close`，并不执行任何实际工作。 若要实际关闭异步操作，请重写`OnClose()`纯虚方法。

## <a name="requirements"></a>要求

**标头：** async.h

**命名空间：** Microsoft::WRL

## <a name="see-also"></a>请参阅

[AsyncBase 类](../windows/asyncbase-class.md)