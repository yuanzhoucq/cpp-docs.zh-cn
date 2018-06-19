---
title: 'Runtimeclass:: Gettrustlevel 方法 |Microsoft 文档'
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
ms.openlocfilehash: bc588950cc8752a7c2b8e1ddf00b2193aaf0f395
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33892626"
---
# <a name="runtimeclassgettrustlevel-method"></a>RuntimeClass::GetTrustLevel 方法

获取当前 RuntimeClass 对象的信任级别。

## <a name="syntax"></a>语法

```cpp
STDMETHOD(GetTrustLevel)(
    _Out_ TrustLevel* trustLvl
);
```

### <a name="parameters"></a>参数

*trustLvl*  
此操作完成后，当前 RuntimeClass 对象的信任级别。

## <a name="return-value"></a>返回值

始终 S_OK。

## <a name="remarks"></a>备注

如果将发出断言错误&#95; &#95;WRL_STRICT&#95; &#95;或&#95; &#95;WRL_FORCE_INSPECTABLE_CLASS_MACRO&#95; &#95;没有定义。

## <a name="requirements"></a>要求

**标头：** implements.h

**命名空间：** Microsoft::WRL

## <a name="see-also"></a>请参阅

[RuntimeClass 类](../windows/runtimeclass-class.md)