---
title: "Interfacetraits:: Cancastto 方法 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: implements/Microsoft::WRL::Details::InterfaceTraits::CanCastTo
dev_langs: C++
helpviewer_keywords: CanCastTo method
ms.assetid: 275847cb-69ea-42bf-910f-05ba6ef8b48d
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 107c89c7643e137b20492f9ae932a736cc0ba603
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="interfacetraitscancastto-method"></a>InterfaceTraits::CanCastTo 方法
支持 WRL 基础结构，不应在代码中直接使用。  
  
## <a name="syntax"></a>语法  
  
```  
  
template<typename T>  
static __forceinline bool CanCastTo(  
   _In_ T* ptr,  
   REFIID riid,  
   _Deref_out_ void **ppv  
);  
  
```  
  
#### <a name="parameters"></a>参数  
 `ptr`  
 指向类型的名称。  
  
 `riid`  
 接口 ID `Base`。  
  
 `ppv`  
 如果此操作成功，`ppv`指向指定的接口`Base`。 否则为`ppv`设置为`nullptr`。  
  
## <a name="return-value"></a>返回值  
 `true`如果此操作是否成功和`ptr`被强制转换为指向的指针`Base`; 否则为`false`。  
  
## <a name="remarks"></a>备注  
 指示是否可以强制的指定的指针转换为指向的指针`Base`。  
  
 有关详细信息`Base`，请参阅中的公共 Typedef 部分[InterfaceTraits 结构](../windows/interfacetraits-structure.md)。  
  
## <a name="requirements"></a>要求  
 **标头：** implements.h  
  
 **Namespace:** Microsoft::WRL::Details  
  
## <a name="see-also"></a>另请参阅  
 [InterfaceTraits 结构](../windows/interfacetraits-structure.md)   
 [Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)