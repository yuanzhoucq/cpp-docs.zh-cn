---
title: "CreateActivationFactory 函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: module/Microsoft::WRL::Details::CreateActivationFactory
dev_langs: C++
helpviewer_keywords: CreateActivationFactory function
ms.assetid: a1a53e04-6757-4faf-a4c8-ecf06e43b959
caps.latest.revision: "2"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e36a76de38290cfd1571f1c5743745561f14e438
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="createactivationfactory-function"></a>CreateActivationFactory 函数
创建为可由 Windows 运行时激活的指定类生成实例的工厂。  
  
## <a name="syntax"></a>语法  
  
```cpp  
template<typename Factory>  
   inline HRESULT STDMETHODCALLTYPE CreateActivationFactory(  
      _In_ unsigned int *flags,        _In_ const CreatorMap* entry,   
      REFIID riid,   
     _Outptr_ IUnknown **ppFactory) throw();  
  
```  
  
#### <a name="parameters"></a>参数  
 `flags`  
 一个或多个组合[RuntimeClassType](../windows/runtimeclasstype-enumeration.md)枚举值。  
  
 `entry`  
 指向[CreatorMap](../windows/creatormap-structure.md) ，包含有关参数的初始化和注册信息`riid`。  
  
 `riid`  
 引用接口 id。  
  
 `ppFactory`  
 如果此操作成功完成，指向的激活工厂。  
  
## <a name="return-value"></a>返回值  
 如果成功，则为 S_OK；否则为指示错误的 HRESULT。  
  
## <a name="remarks"></a>备注  
 如果将发出断言错误模板参数`Factory`不派生自接口 IActivationFactory。  
  
## <a name="requirements"></a>要求  
 **标头：** module.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>另请参阅  
 [Microsoft::WRL::Wrappers::Details 命名空间](../windows/microsoft-wrl-wrappers-details-namespace.md)