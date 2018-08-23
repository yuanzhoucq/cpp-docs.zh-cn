---
title: 'Implements:: cancastto 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Implements::CanCastTo
dev_langs:
- C++
helpviewer_keywords:
- CanCastTo method
ms.assetid: a8e85c7d-4dcd-446d-bebc-a97da46ce44a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 328691877a3b129c852460f8f68cdd3db4974e6f
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42595294"
---
# <a name="implementscancastto-method"></a>Implements::CanCastTo 方法

获取一个指向指定接口。

## <a name="syntax"></a>语法

```cpp
__forceinline HRESULT CanCastTo(
   REFIID riid,
   _Deref_out_ void **ppv
);
```

### <a name="parameters"></a>参数

*riid*  
对接口 id。

*ppv*  
如果成功，指向接口由指定*riid*。

## <a name="return-value"></a>返回值

如果成功，则为 S_OK否则为一个 HRESULT，指示错误，例如 E_NOINTERFACE。

## <a name="remarks"></a>备注

这是执行 QueryInterface 操作内部帮助器函数。

## <a name="requirements"></a>要求

**标头：** implements.h

**命名空间：** Microsoft::WRL

## <a name="see-also"></a>请参阅

[Implements 结构](../windows/implements-structure.md)