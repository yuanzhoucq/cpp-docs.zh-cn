---
title: ActivationFactoryCallback 函数 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::ActivationFactoryCallback
dev_langs:
- C++
helpviewer_keywords:
- ActivationFactoryCallback function
ms.assetid: dd40c79b-1273-4f2a-8c24-ae9926fb4fd9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 62efb2b1aa2cd2caa0c5701696689ea3df19f962
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46443602"
---
# <a name="activationfactorycallback-function"></a>ActivationFactoryCallback 函数

支持 WRL 基础结构，不应在代码中直接使用。

## <a name="syntax"></a>语法

```cpp
inline HRESULT STDAPICALLTYPE ActivationFactoryCallback(
   HSTRING activationId,
   IActivationFactory **ppFactory
);
```

### <a name="parameters"></a>参数

*activationId*<br/>
一个字符串，指定运行时类名称的句柄。

*ppFactory*<br/>
此操作完成后，对应于参数的激活工厂*activationId*。

## <a name="return-value"></a>返回值

如果成功，则为 S_OK；否则为描述失败的 HRESULT。 可能会失败的 Hresult 是 CLASS_E_CLASSNOTAVAILABLE 和 E_INVALIDARG。

## <a name="remarks"></a>备注

获取激活工厂指定的激活 id。

Windows 运行时调用此回调函数来请求由其运行时类名称指定的对象。

## <a name="requirements"></a>要求

**标头：** module.h

**Namespace:** Microsoft::WRL::Details

## <a name="see-also"></a>请参阅

[Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)