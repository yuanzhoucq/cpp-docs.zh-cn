---
title: 'Runtimeclass:: Gettrustlevel 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClass::GetTrustLevel
dev_langs:
- C++
helpviewer_keywords:
- GetTrustLevel method
ms.assetid: bd90407e-6dd7-41c3-9ea0-c402c276014a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c714f37a53e111c90333352610fd73532ac86fe7
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42599827"
---
# <a name="runtimeclassgettrustlevel-method"></a>RuntimeClass::GetTrustLevel 方法

获取当前的信任级别**RuntimeClass**对象。

## <a name="syntax"></a>语法

```cpp
STDMETHOD(GetTrustLevel)(
    _Out_ TrustLevel* trustLvl
);
```

### <a name="parameters"></a>参数

*trustLvl*  
此操作完成后，当前的信任级别**RuntimeClass**对象。

## <a name="return-value"></a>返回值

始终返回 S_OK。

## <a name="remarks"></a>备注

如果发出断言错误`__WRL_STRICT__`或`__WRL_FORCE_INSPECTABLE_CLASS_MACRO__`并不定义。

## <a name="requirements"></a>要求

**标头：** implements.h

**命名空间：** Microsoft::WRL

## <a name="see-also"></a>请参阅

[RuntimeClass 类](../windows/runtimeclass-class.md)