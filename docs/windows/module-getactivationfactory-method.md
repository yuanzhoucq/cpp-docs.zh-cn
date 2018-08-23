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
ms.openlocfilehash: 0e87ea3b0e44732d4271385073c48fd92e1aa114
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42608922"
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

*pActivatibleClassId*  
运行时类的 IID。

*ppIFactory*  
指定运行时类的 IActivationFactory。

*服务器名称*  
当前模块中类工厂的子集名称。 指定中使用的服务器名称[ActivatableClassWithFactoryEx](../windows/activatableclass-macros.md)宏，或指定**nullptr**若要获取默认服务器名称。

## <a name="return-value"></a>返回值

如果成功，则为 S_OK；否则为 GetActivationFactory 返回的 HRESULT。

## <a name="requirements"></a>要求

**标头：** module.h

**命名空间：** Microsoft::WRL

## <a name="see-also"></a>请参阅

[Module 类](../windows/module-class.md)  
[ActivatableClass 宏](../windows/activatableclass-macros.md)