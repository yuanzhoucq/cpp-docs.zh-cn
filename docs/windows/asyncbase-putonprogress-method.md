---
title: 'Asyncbase:: Putonprogress 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::PutOnProgress
dev_langs:
- C++
helpviewer_keywords:
- PutOnProgress method
ms.assetid: 1f5f180e-eb5a-4afe-ac16-69dbf36f0383
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8b2bc46f916e4aaaedc74e8b6d94faafa1ead3b9
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42595482"
---
# <a name="asyncbaseputonprogress-method"></a>AsyncBase::PutOnProgress 方法

为指定的值设置的进度事件处理程序的地址。

## <a name="syntax"></a>语法

```cpp
STDMETHOD(
   PutOnProgress
)(TProgress* progressHandler);
```

### <a name="parameters"></a>参数

*progressHandler*  
进度事件处理程序设置为地址。

## <a name="return-value"></a>返回值

如果成功，则为 S_OK否则为 E_ILLEGAL_METHOD_CALL。

## <a name="requirements"></a>要求

**标头：** async.h

**命名空间：** Microsoft::WRL

## <a name="see-also"></a>请参阅

[AsyncBase 类](../windows/asyncbase-class.md)