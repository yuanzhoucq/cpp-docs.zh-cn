---
title: "Asyncbase:: Getoncomplete 方法 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: async/Microsoft::WRL::AsyncBase::GetOnComplete
dev_langs: C++
helpviewer_keywords: GetOnComplete method
ms.assetid: f06ae02d-9a88-41d2-b749-bdc1a7ff8748
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 041c5960f0ae126252a31da3c71826e1e47a0385
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="asyncbasegetoncomplete-method"></a>AsyncBase::GetOnComplete 方法
将当前的完成事件处理程序的地址复制到指定的变量。  
  
## <a name="syntax"></a>语法  
  
```  
STDMETHOD(  
   GetOnComplete  
)(TComplete** completeHandler);  
```  
  
#### <a name="parameters"></a>参数  
 `completeHandler`  
 存储当前完成事件处理程序的地址的位置。  
  
## <a name="return-value"></a>返回值  
 如果成功，则则为 S_OK否则为 E_ILLEGAL_METHOD_CALL。  
  
## <a name="requirements"></a>惠?  
 **标头：** async.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>请参阅  
 [AsyncBase 类](../windows/asyncbase-class.md)