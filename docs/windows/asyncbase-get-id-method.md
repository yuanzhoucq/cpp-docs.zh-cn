---
title: "Asyncbase:: Get_id 方法 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: async/Microsoft::WRL::AsyncBase::get_Id
dev_langs: C++
helpviewer_keywords: get_Id method
ms.assetid: 591d8366-ea76-4deb-9278-9d3bc394a42b
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f90a3b57f1691db67b6ba5a62704b91bd8e4eb7b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="asyncbasegetid-method"></a>AsyncBase::get_Id 方法
检索异步操作的句的柄。  
  
## <a name="syntax"></a>语法  
  
```  
STDMETHOD(  
   get_Id  
)(unsigned int *id) override;  
```  
  
#### <a name="parameters"></a>参数  
 `id`  
 句柄为要存储的位置。  
  
## <a name="return-value"></a>返回值  
 如果成功，则则为 S_OK否则为 E_ILLEGAL_METHOD_CALL。  
  
## <a name="remarks"></a>备注  
 此方法实现 IAsyncInfo::get_Id。  
  
## <a name="requirements"></a>要求  
 **标头：** async.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>另请参阅  
 [AsyncBase 类](../windows/asyncbase-class.md)