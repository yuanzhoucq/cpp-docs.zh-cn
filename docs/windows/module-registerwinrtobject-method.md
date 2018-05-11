---
title: 'Module:: registerwinrtobject 方法 |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::RegisterWinRTObject
dev_langs:
- C++
helpviewer_keywords:
- RegisterWinRTObject method
ms.assetid: a2782c9c-b9c5-4e4b-9c8d-ef513aea20c5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 097bf70ebd280d9494ff70ea1d80f53615f3d898
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="moduleregisterwinrtobject-method"></a>Module::RegisterWinRTObject 方法
注册一个或多个 Windows 运行时对象，以便其他应用程序可以连接到它们。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT RegisterWinRTObject(const wchar_t* serverName,  
   wchar_t** activatableClassIds,  
   WINRT_REGISTRATION_COOKIE* cookie,  
   unsigned int count)  
```  
  
#### <a name="parameters"></a>参数  
 `serverName`  
 指定受此操作影响的对象子集的名称。  
  
 `activatableClassIds`  
 要注册的可激活 CLSID 的数组。  
  
 `cookie`  
 标识已注册类对象的值。 此值以后将用于撤销注册。  
  
 `count`  
 要注册的对象的数量。  
  
## <a name="return-value"></a>返回值  
 如果成功，则为 S_OK；否则为指示操作失败原因的 HRESULT（如 CO_E_OBJISREG）。  
  
## <a name="requirements"></a>要求  
 **标头：** module.h  
  
 **命名空间：** Microsoft::WRL
 
 ## <a name="see-also"></a>请参阅
 [Module 类](../windows/module-class.md)