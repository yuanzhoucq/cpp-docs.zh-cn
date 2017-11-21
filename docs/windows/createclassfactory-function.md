---
title: "CreateClassFactory 函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: module/Microsoft::WRL::Details::CreateClassFactory
dev_langs: C++
helpviewer_keywords: CreateClassFactory function
ms.assetid: 772d5d1b-8872-4745-81ca-521a39564713
caps.latest.revision: "2"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5ac438e233c675b6d650af83354edd36f877602d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
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
  
#### <a name="parameters"></a>参数  
 `flags`  
 一个或多个组合[RuntimeClassType](../windows/runtimeclasstype-enumeration.md)枚举值。  
  
 `entry`  
 指向[CreatorMap](../windows/creatormap-structure.md) ，包含有关参数的初始化和注册信息`riid`。  
  
 `riid`  
 引用接口 id。  
  
 `ppFactory`  
 如果此操作成功，完成到类工厂的指针。  
  
## <a name="return-value"></a>返回值  
 如果成功，则为 S_OK；否则为指示错误的 HRESULT。  
  
## <a name="remarks"></a>备注  
 如果将发出断言错误模板参数`Factory`不派生自接口 IClassFactory。  
  
## <a name="requirements"></a>要求  
 **标头：** module.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>另请参阅  
 [Microsoft::WRL::Wrappers::Details 命名空间](../windows/microsoft-wrl-wrappers-details-namespace.md)