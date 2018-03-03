---
title: "GetActivationFactory 函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::GetActivationFactory
- client/ABI::Windows::Foundation::GetActivationFactory
- client/Windows::Foundation::GetActivationFactory
dev_langs:
- C++
helpviewer_keywords:
- GetActivationFactory function
ms.assetid: 5736d285-6beb-42aa-8788-e261c0010afe
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6419ef4d48c3f151f8acfb49d40e10853f5d17f7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="getactivationfactory-function"></a>GetActivationFactory 函数
检索由模板参数指定的类型的激活工厂。  
  
## <a name="syntax"></a>语法  
  
```  
template<  
   typename T  
>  
inline HRESULT GetActivationFactory(  
   _In_ HSTRING activatableClassId,  
   _Out_ Microsoft::WRL::Details::ComPtrRef<T> factory  
);  
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 一个模板参数，指定的激活工厂的类型。  
  
 `activatableClassId`  
 激活工厂可以生成的类名称。  
  
 `factory`  
 此操作完成后，对类型的激活工厂的引用`T`。  
  
## <a name="return-value"></a>返回值  
 如果成功，则则为 S_OK否则为该值指示此操作失败的原因的 HRESULT 错误。  
  
## <a name="requirements"></a>惠?  
 **标头：** client.h  
  
 **Namespace:** windows:: foundation  
  
## <a name="see-also"></a>请参阅  
 [Windows::Foundation 命名空间](../windows/windows-foundation-namespace.md)