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
ms.openlocfilehash: adcec3f4a531a6c48e0995468994900124746e4b
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/09/2018
ms.locfileid: "40015126"
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