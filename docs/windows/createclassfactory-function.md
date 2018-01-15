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
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0ac522c2997f6c170e76c462626bb98a290a7dc4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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
  
## <a name="requirements"></a>惠?  
 **标头：** module.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>请参阅  
 [Microsoft::WRL::Wrappers::Details 命名空间](../windows/microsoft-wrl-wrappers-details-namespace.md)