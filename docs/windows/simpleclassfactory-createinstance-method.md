---
title: 'Simpleclassfactory:: Createinstance 方法 |Microsoft 文档'
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
ms.openlocfilehash: 8a31d364a6464962b8243cfaced03131a20f9324
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33892743"
---
# <a name="simpleclassfactorycreateinstance-method"></a>SimpleClassFactory::CreateInstance 方法

创建指定的接口的实例。

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
必须是`nullptr`; 否则为返回值是 CLASS_E_NOAGGREGATION。

SimpleClassFactory 不支持聚合。 如果聚合受支持，且正在创建的对象为聚合时，属于`pUnkOuter`将指向的聚合控制的 IUnknown 接口的指针。

*riid*  
接口的对象 ID 来创建。

*ppvObject*  
此操作完成后，向指定的对象的实例的指针`riid`参数。

## <a name="return-value"></a>返回值

如果成功，则为 S_OK；否则为指示错误的 HRESULT。

## <a name="remarks"></a>备注

如果&#95; &#95;WRL_STRICT&#95; &#95;是定义，将断言发出错误如果基类中类模板参数指定不派生自[RuntimeClass](../windows/runtimeclass-class.md)，或者因配置不与 ClassicCom 或WinRtClassicComMix [RuntimeClassType](../windows/runtimeclasstype-enumeration.md)枚举值。

## <a name="requirements"></a>要求

**标头：** module.h

**命名空间：** Microsoft::WRL

## <a name="see-also"></a>请参阅

[SimpleClassFactory 类](../windows/simpleclassfactory-class.md)