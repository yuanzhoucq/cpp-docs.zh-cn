---
title: 'Runtimeclass:: Addref 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClass::AddRef
dev_langs:
- C++
helpviewer_keywords:
- AddRef method
ms.assetid: 9c705749-680b-4308-bbec-5b601e8e7dbd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 45dcc46077689d5485cc72f9238a6064a9589eac
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42589130"
---
# <a name="runtimeclassaddref-method"></a>RuntimeClass::AddRef 方法

当前的引用计数递增**RuntimeClass**对象。

## <a name="syntax"></a>语法

```cpp
STDMETHOD_(
   ULONG,
   AddRef
)();
```

## <a name="return-value"></a>返回值

如果成功，则为 S_OK；否则为指示错误的 HRESULT。

## <a name="requirements"></a>要求

**标头：** implements.h

**命名空间：** Microsoft::WRL

## <a name="see-also"></a>请参阅

[RuntimeClass 类](../windows/runtimeclass-class.md)