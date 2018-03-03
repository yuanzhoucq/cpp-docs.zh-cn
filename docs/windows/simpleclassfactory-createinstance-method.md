---
title: "Simpleclassfactory:: Createinstance 方法 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::SimpleClassFactory::CreateInstance
dev_langs:
- C++
helpviewer_keywords:
- CreateInstance method
ms.assetid: 17b7947a-2608-49d9-b730-fef76501c9bc
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 68778eb1b5421cfcf22261d8b1c1efd99bc32c50
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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

如果 &#95; &#95;WRL_STRICT &#95; &#95;是定义，将断言发出错误如果基类中类模板参数指定不派生自[RuntimeClass](../windows/runtimeclass-class.md)，或者因配置不与 ClassicCom 或 WinRtClassicComMix [RuntimeClassType](../windows/runtimeclasstype-enumeration.md)枚举值。

## <a name="requirements"></a>惠?

**标头：** module.h

**命名空间：** Microsoft::WRL

## <a name="see-also"></a>请参阅

[SimpleClassFactory 类](../windows/simpleclassfactory-class.md)