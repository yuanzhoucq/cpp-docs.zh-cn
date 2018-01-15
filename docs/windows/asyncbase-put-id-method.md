---
title: "Asyncbase:: Put_id 方法 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: async/Microsoft::WRL::AsyncBase::put_Id
dev_langs: C++
helpviewer_keywords: put_Id method
ms.assetid: aebad85f-4774-42de-b625-a9cf5f65cb4e
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 60135d69f6f3f8b73256fd65d89651351bd100e5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="asyncbaseputid-method"></a>AsyncBase::put_Id 方法
设置异步操作的句的柄。  
  
## <a name="syntax"></a>语法  
  
```  
STDMETHOD(  
   put_Id  
)(const unsigned int id);  
```  
  
#### <a name="parameters"></a>参数  
 `id`  
 非零的句柄。  
  
## <a name="return-value"></a>返回值  
 如果成功，则则为 S_OK否则为为 E_INVALIDARG 或 E_ILLEGAL_METHOD_CALL。  
  
## <a name="requirements"></a>惠?  
 **标头：** async.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>请参阅  
 [AsyncBase 类](../windows/asyncbase-class.md)