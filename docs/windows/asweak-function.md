---
title: "AsWeak 函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::AsWeak
dev_langs:
- C++
helpviewer_keywords:
- AsWeak function
ms.assetid: a6f10cfc-c1d6-4761-adb9-1a119cc99913
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2bc994c502a806fcca0ead9a5c73aa6f8b5dd02e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="asweak-function"></a>AsWeak 函数
检索对指定实例的弱引用。  
  
## <a name="syntax"></a>语法  
  
```  
template<  
   typename T  
>  
HRESULT AsWeak(  
   _In_ T* p,  
   _Out_ WeakRef* pWeak  
);  
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 指向参数的类型的指针`p`。  
  
 `p`  
 类型的实例。  
  
 `pWeak`  
 此操作完成后，对参数的弱引用指向的指针`p`。  
  
## <a name="return-value"></a>返回值  
 则为 S_OK，如果此操作成功，则否则为的错误 HRESULT，该值指示失败的原因。  
  
## <a name="requirements"></a>惠?  
 **标头：** client.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>请参阅  
 [Microsoft::WRL Namespace](../windows/microsoft-wrl-namespace.md)