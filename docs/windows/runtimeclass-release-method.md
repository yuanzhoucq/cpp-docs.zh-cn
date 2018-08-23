---
title: 'Runtimeclass:: Release 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClass::Release
dev_langs:
- C++
helpviewer_keywords:
- Release method
ms.assetid: 0bd6f9e2-ad90-4de6-adef-a6286f458cb6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b0cb7af376e577a53f888425519108dedf01b7f1
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42612047"
---
# <a name="runtimeclassrelease-method"></a>RuntimeClass::Release 方法

执行 COM 释放操作对当前**RuntimeClass**对象。

## <a name="syntax"></a>语法

```cpp
STDMETHOD_(
   ULONG,
   Release
)();
```

## <a name="return-value"></a>返回值

如果成功，则为 S_OK；否则为指示错误的 HRESULT。

## <a name="remarks"></a>备注

如果引用计数变为零， **RuntimeClass**删除对象。

## <a name="requirements"></a>要求

**标头：** implements.h

**命名空间：** Microsoft::WRL

## <a name="see-also"></a>请参阅

[RuntimeClass 类](../windows/runtimeclass-class.md)