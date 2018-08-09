---
title: 'Simpleclassfactory:: Createinstance 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::SimpleClassFactory::CreateInstance
dev_langs:
- C++
helpviewer_keywords:
- CreateInstance method
ms.assetid: 17b7947a-2608-49d9-b730-fef76501c9bc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f25e85e59769f822a6c732cc0911c564c0104f96
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39651075"
---
# <a name="simpleclassfactorycreateinstance-method"></a>SimpleClassFactory::CreateInstance 方法

创建指定接口的实例。

## <a name="syntax"></a>语法

```cpp
STDMETHOD( CreateInstance )(
   _Inout_opt_ IUnknown* pUnkOuter,
   REFIID riid,
   _Deref_out_ void** ppvObject
);
```

### <a name="parameters"></a>参数

*pUnkOuter*  
必须是**nullptr**; 否则为返回值是 CLASS_E_NOAGGREGATION。

SimpleClassFactory 不支持聚合。 如果受支持聚合，并且正在创建的对象是一个聚合的组成部分*pUnkOuter*是一个指向控制`IUnknown`聚合的接口。

*riid*  
若要创建的对象 ID 的接口。

*ppvObject*  
此操作完成后，指向由指定的对象的实例*riid*参数。

## <a name="return-value"></a>返回值

如果成功，则为 S_OK；否则为指示错误的 HRESULT。

## <a name="remarks"></a>备注

如果&#95; &#95;WRL_STRICT&#95; &#95;是定义，断言错误发出如果类模板参数中指定的基类不派生自[RuntimeClass](../windows/runtimeclass-class.md)，或者因配置不与 ClassicCom 或WinRtClassicComMix [RuntimeClassType](../windows/runtimeclasstype-enumeration.md)枚举值。

## <a name="requirements"></a>要求

**标头：** module.h

**命名空间：** Microsoft::WRL

## <a name="see-also"></a>请参阅
 [SimpleClassFactory 类](../windows/simpleclassfactory-class.md)