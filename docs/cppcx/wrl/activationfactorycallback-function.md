---
title: ActivationFactoryCallback 函数
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::ActivationFactoryCallback
helpviewer_keywords:
- ActivationFactoryCallback function
ms.assetid: dd40c79b-1273-4f2a-8c24-ae9926fb4fd9
ms.openlocfilehash: 4743e7724c5aba4171cb017654267afaac676f24
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59021600"
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

**命名空间：** Microsoft::WRL::Details

## <a name="see-also"></a>请参阅

[Microsoft::WRL::Details 命名空间](microsoft-wrl-details-namespace.md)