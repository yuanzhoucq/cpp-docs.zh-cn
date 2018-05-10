---
title: 'Module:: getactivationfactory 方法 |Microsoft 文档'
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
ms.openlocfilehash: 837cb68173ca1994de6bc560882d617bb3aa03e0
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="modulegetactivationfactory-method"></a>Module::GetActivationFactory 方法
获取模块的激活工厂。  
  
## <a name="syntax"></a>语法  
  
```  
WRL_NOTHROW HRESULT GetActivationFactory(  
   _In_ HSTRING pActivatibleClassId,  
   _Deref_out_ IActivationFactory **ppIFactory,  
   wchar_t* serverName = nullptr  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pActivatibleClassId`  
 运行时类的 IID。  
  
 `ppIFactory`  
 指定运行时类的 IActivationFactory。  
  
 `serverName`  
 当前模块中类工厂的子集名称。 指定服务器名称中使用[ActivatableClassWithFactoryEx](../windows/activatableclass-macros.md)宏，或指定`nullptr`以获取默认服务器名称。  
  
## <a name="return-value"></a>返回值  
 如果成功，则为 S_OK；否则为 GetActivationFactory 返回的 HRESULT。  
  
## <a name="requirements"></a>要求  
 **标头：** module.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>请参阅  
[Module 类](../windows/module-class.md) [ActivatableClass 宏](../windows/activatableclass-macros.md)