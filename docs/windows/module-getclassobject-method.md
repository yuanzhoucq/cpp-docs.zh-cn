---
title: 'Module:: getclassobject 方法 |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::GetClassObject
dev_langs:
- C++
helpviewer_keywords:
- GetClassObject method
ms.assetid: 95b0de1b-f728-4f96-9f44-f6ea71ce56e4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9205b04fc27e1c6e0e6133a08c3c2f69ffdfc314
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="modulegetclassobject-method"></a>Module::GetClassObject 方法
检索类工厂的缓存。  
  
## <a name="syntax"></a>语法  
  
```  
 HRESULT GetClassObject(  
   REFCLSID clsid,  
   REFIID riid,  
   _Deref_out_ void **ppv,  
   wchar_t* serverName = nullptr  
);  
```  
  
#### <a name="parameters"></a>参数  
 `clsid`  
 类 ID。  
  
 `riid`  
 您请求的接口 ID。  
  
 `ppv`  
 指向返回对象的指针。  
  
 `serverName`  
 在 `ActivatableClassWithFactory`、`ActivatableClassWithFactoryEx` 或 `ActivatableClass` 宏中指定的服务器名称；或用于获取默认服务器名称的 `nullptr`。  
  
## <a name="return-value"></a>返回值  
  
## <a name="remarks"></a>备注  
 仅对 COM 而不是 Windows 运行时使用此方法。 此方法仅公开 IClassFactory 方法。  
  
## <a name="requirements"></a>要求  
 **标头：** module.h  
  
 **命名空间：** Microsoft::WRL
 
 ## <a name="see-also"></a>请参阅
 [Module 类](../windows/module-class.md)