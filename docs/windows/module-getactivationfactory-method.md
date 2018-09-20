---
title: 'Module:: getactivationfactory 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::GetActivationFactory
dev_langs:
- C++
helpviewer_keywords:
- GetActivationFactory method
ms.assetid: 59da8844-072e-414b-b89c-1db1cc4fd81d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 995594ee48e6ca408e88d9ab14968d88b536d309
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46403499"
---
# <a name="modulegetactivationfactory-method"></a>Module::GetActivationFactory 方法

获取模块的激活工厂。

## <a name="syntax"></a>语法

```cpp
WRL_NOTHROW HRESULT GetActivationFactory(
   _In_ HSTRING pActivatibleClassId,
   _Deref_out_ IActivationFactory **ppIFactory,
   wchar_t* serverName = nullptr
);
```

### <a name="parameters"></a>参数

*pActivatibleClassId*<br/>
运行时类的 IID。

*ppIFactory*<br/>
指定运行时类的 IActivationFactory。

*服务器名称*<br/>
当前模块中类工厂的子集名称。 指定中使用的服务器名称[ActivatableClassWithFactoryEx](../windows/activatableclass-macros.md)宏，或指定**nullptr**若要获取默认服务器名称。

## <a name="return-value"></a>返回值

如果成功，则为 S_OK；否则为 GetActivationFactory 返回的 HRESULT。

## <a name="requirements"></a>要求

**标头：** module.h

**命名空间：** Microsoft::WRL

## <a name="see-also"></a>请参阅

[Module 类](../windows/module-class.md)<br/>
[ActivatableClass 宏](../windows/activatableclass-macros.md)