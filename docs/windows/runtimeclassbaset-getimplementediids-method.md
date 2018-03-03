---
title: "Runtimeclassbaset:: Getimplementediids 方法 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::RuntimeClassBaseT::GetImplementedIIDS
dev_langs:
- C++
helpviewer_keywords:
- GetImplementedIIDS method
ms.assetid: adae54da-521d-4add-87f5-242fbd85f33b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 25410ac57e1812d3f4648151afff4f97d413689b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="runtimeclassbasetgetimplementediids-method"></a>RuntimeClassBaseT::GetImplementedIIDS 方法
支持 WRL 基础结构，不应在代码中直接使用。  
  
## <a name="syntax"></a>语法  
  
```  
template<  
   typename T  
>  
__forceinline static HRESULT GetImplementedIIDS(  
   _In_ T* implements,  
   _Out_ ULONG *iidCount,  
   _Deref_out_ _Deref_post_cap_(*iidCount) IID **iids  
);  
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 `implements` 参数的类型。  
  
 `implements`  
 为参数指定的类型的指针`T`。  
  
 `iidCount`  
 接口 Id，以检索最大数量。  
  
 `iids`  
 如果此操作成功完成操作，接口实现的类型的 Id 的数组`T`。  
  
## <a name="return-value"></a>返回值  
 如果成功，则则为 S_OK否则为描述错误的 HRESULT。  
  
## <a name="remarks"></a>备注  
 检索接口实现由指定类型的 Id 的数组。  
  
## <a name="requirements"></a>惠?  
 **标头：** implements.h  
  
 **Namespace:** Microsoft::WRL::Details  
  
## <a name="see-also"></a>请参阅  
 [RuntimeClassBaseT 结构](../windows/runtimeclassbaset-structure.md)