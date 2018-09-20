---
title: CreateClassFactory 函数 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::CreateClassFactory
dev_langs:
- C++
helpviewer_keywords:
- CreateClassFactory function
ms.assetid: 772d5d1b-8872-4745-81ca-521a39564713
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c1d7c3741af7f5a0ea3a66d491f4aecc2afc8cb9
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46392185"
---
# <a name="createclassfactory-function"></a>CreateClassFactory 函数

创建为指定类生成实例的工厂。

## <a name="syntax"></a>语法

```cpp
template<typename Factory>
inline HRESULT STDMETHODCALLTYPE CreateClassFactory(
   _In_ unsigned int *flags,
   _In_ const CreatorMap* entry,
   REFIID riid,
   _Outptr_ IUnknown **ppFactory
) throw();
```

### <a name="parameters"></a>参数

*flags*<br/>
一个或多个组合[RuntimeClassType](../windows/runtimeclasstype-enumeration.md)枚举值。

*entry*<br/>
指向[CreatorMap](../windows/creatormap-structure.md)包含有关参数的初始化和注册信息*riid*。

*riid*<br/>
引用接口 id。

*ppFactory*<br/>
如果此操作成功完成，指向类工厂。

## <a name="return-value"></a>返回值

如果成功，则为 S_OK；否则为指示错误的 HRESULT。

## <a name="remarks"></a>备注

如果发出断言错误模板参数*工厂*不会派生自接口`IClassFactory`。

## <a name="requirements"></a>要求

**标头：** module.h

**命名空间：** Microsoft::WRL

## <a name="see-also"></a>请参阅

[Microsoft::WRL::Wrappers::Details 命名空间](../windows/microsoft-wrl-wrappers-details-namespace.md)