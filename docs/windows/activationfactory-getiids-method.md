---
title: "Activationfactory:: Getiids 方法 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: module/Microsoft::WRL::ActivationFactory::GetIids
dev_langs: C++
helpviewer_keywords: GetIids method
ms.assetid: 0983d709-d155-4d65-aae4-5b2c8bb0fede
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: da0ab5960b84b16f8eb05679e0afdb9a85a1955d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="activationfactorygetiids-method"></a>ActivationFactory::GetIids 方法
检索已实现接口 ID 的数组。  
  
## <a name="syntax"></a>语法  
  
```  
STDMETHOD(  
   GetIids  
)(_Out_ ULONG *iidCount, _Deref_out_ _Deref_post_cap_(*iidCount) IID **iids);  
```  
  
#### <a name="parameters"></a>参数  
 `iidCount`  
 此操作完成后，`iids` 数组中接口 ID 的数量。  
  
 `iids`  
 此操作完成后，已实现接口 ID 的数组。  
  
## <a name="return-value"></a>返回值  
 如果成功，则为 S_OK；否则为描述失败的 HRESULT。 E_OUTOFMEMORY 是可能的失败 HRESULT。  
  
## <a name="requirements"></a>惠?  
 **标头：** module.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>请参阅  
 [ActivationFactory 类](../windows/activationfactory-class.md)