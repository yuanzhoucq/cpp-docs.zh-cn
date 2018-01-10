---
title: "ActivateInstance 函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- client/Windows::Foundation::ActivateInstance
- client/ABI::Windows::Foundation::ActivateInstance
dev_langs: C++
helpviewer_keywords: ActivateInstance function
ms.assetid: 8cfd1dd9-5fda-4cc2-acf8-d40e783b3875
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 051eb51a4461d1b3f9ab180507022cdfa955f0ad
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="activateinstance-function"></a>ActivateInstance 函数
注册并检索在指定的类 id。 定义的指定类型的实例  
  
## <a name="syntax"></a>语法  
  
```  
template<  
   typename T  
>  
inline HRESULT ActivateInstance(  
   _In_ HSTRING activatableClassId,  
   _Out_ Microsoft::WRL::Details::ComPtrRef<T> instance  
);  
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 要激活的类型。  
  
 `activatableClassId`  
 定义参数的类 ID 的名称`T`。  
  
 `instance`  
 此操作完成后，对的实例的引用`T`。  
  
## <a name="return-value"></a>返回值  
 如果成功，则则为 S_OK否则为指示错误的原因的 HRESULT 错误。  
  
## <a name="requirements"></a>惠?  
 **标头：** client.h  
  
 **Namespace:** windows:: foundation  
  
## <a name="see-also"></a>请参阅  
 [Windows::Foundation 命名空间](../windows/windows-foundation-namespace.md)