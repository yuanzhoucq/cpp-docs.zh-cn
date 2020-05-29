---
title: ActivationFactoryCallback 函数
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::ActivationFactoryCallback
helpviewer_keywords:
- ActivationFactoryCallback function
ms.assetid: dd40c79b-1273-4f2a-8c24-ae9926fb4fd9
ms.openlocfilehash: 0be4bebcc561cdf1df3f2502c8cc1927bdc65564
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214209"
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

### <a name="parameters"></a>parameters

*activationId*<br/>
用于指定运行时类名称的字符串的句柄。

*ppFactory*<br/>
此操作完成后，与参数*activationId*相对应的激活工厂。

## <a name="return-value"></a>返回值

如果成功，则为 S_OK；否则为描述失败的 HRESULT。 CLASS_E_CLASSNOTAVAILABLE 和 E_INVALIDARG 可能会出现故障 Hresult。

## <a name="remarks"></a>备注

获取指定激活 ID 的激活工厂。

Windows 运行时调用此回调函数以请求由其运行时类名称指定的对象。

## <a name="requirements"></a>要求

**标头：** 模块。h

**命名空间：** Microsoft：： WRL：:D etails

## <a name="see-also"></a>另请参阅

[Microsoft::WRL::Details 命名空间](microsoft-wrl-details-namespace.md)
