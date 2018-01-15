---
title: "Module:: getactivationfactory 方法 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: module/Microsoft::WRL::Module::GetActivationFactory
dev_langs: C++
helpviewer_keywords: GetActivationFactory method
ms.assetid: 59da8844-072e-414b-b89c-1db1cc4fd81d
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5d5c5ca4d470f52ff9dde862cc99b10a3459cd0c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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
  
## <a name="requirements"></a>惠?  
 **标头：** module.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>请参阅  
[Module 类](../windows/module-class.md) [ActivatableClass 宏](../windows/activatableclass-macros.md)