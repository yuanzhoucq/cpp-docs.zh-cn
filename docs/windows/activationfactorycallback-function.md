---
title: "ActivationFactoryCallback 函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: module/Microsoft::WRL::Details::ActivationFactoryCallback
dev_langs: C++
helpviewer_keywords: ActivationFactoryCallback function
ms.assetid: dd40c79b-1273-4f2a-8c24-ae9926fb4fd9
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e88a6f9cb89746cd0380587789fbdd68f80d5e36
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="activationfactorycallback-function"></a>ActivationFactoryCallback 函数
支持 WRL 基础结构，不应在代码中直接使用。  
  
## <a name="syntax"></a>语法  
  
```  
inline HRESULT STDAPICALLTYPE ActivationFactoryCallback(  
   HSTRING activationId,  
   IActivationFactory **ppFactory  
);  
```  
  
#### <a name="parameters"></a>参数  
 `activationId`  
 一个字符串，指定运行时类名称的句柄。  
  
 `ppFactory`  
 此操作完成后，对应于参数的激活工厂`activationId`。  
  
## <a name="return-value"></a>返回值  
 如果成功，则为 S_OK；否则为描述失败的 HRESULT。 可能失败的 hresult 映射为 CLASS_E_CLASSNOTAVAILABLE 和 E_INVALIDARG。  
  
## <a name="remarks"></a>备注  
 获取指定的激活 id。 激活工厂  
  
 Windows 运行时调用此回调函数来请求由其运行时类名称指定的对象。  
  
## <a name="requirements"></a>惠?  
 **标头：** module.h  
  
 **Namespace:** Microsoft::WRL::Details  
  
## <a name="see-also"></a>请参阅  
 [Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)