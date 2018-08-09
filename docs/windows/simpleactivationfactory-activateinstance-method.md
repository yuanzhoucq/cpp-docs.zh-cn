---
title: 'Simpleactivationfactory:: Activateinstance 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::SimpleActivationFactory::ActivateInstance
dev_langs:
- C++
helpviewer_keywords:
- ActivateInstance method
ms.assetid: 4f836e51-5a6c-4bad-b871-9f25199298b4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: fe1342c3927183ae5eec30c8dd0a40ee95f37277
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39646557"
---
# <a name="simpleactivationfactoryactivateinstance-method"></a>SimpleActivationFactory::ActivateInstance 方法

创建指定接口的实例。

## <a name="syntax"></a>语法

```cpp
STDMETHOD( ActivateInstance )(
    _Deref_out_ IInspectable **ppvObject
);
```

### <a name="parameters"></a>参数

*ppvObject*  
此操作完成后，指向由指定的对象的实例`Base`类模板参数。

## <a name="return-value"></a>返回值

如果成功，则为 S_OK；否则为指示错误的 HRESULT。

## <a name="remarks"></a>备注

如果&#95; &#95;WRL_STRICT&#95; &#95;是定义，断言错误发出如果类模板参数中指定的基类不派生自[RuntimeClass](../windows/runtimeclass-class.md)，或者因配置不与 WinRt 或WinRtClassicComMix [RuntimeClassType](../windows/runtimeclasstype-enumeration.md)枚举值。

## <a name="requirements"></a>要求

**标头：** module.h

**命名空间：** Microsoft::WRL

## <a name="see-also"></a>请参阅
 [SimpleActivationFactory 类](../windows/simpleactivationfactory-class.md)