---
title: 'Asyncbase:: Getoncomplete 方法 |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::GetOnComplete
dev_langs:
- C++
helpviewer_keywords:
- GetOnComplete method
ms.assetid: f06ae02d-9a88-41d2-b749-bdc1a7ff8748
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: fa1bf81c8b377da44fb4b81cdb2b0142e90032e0
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
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
  
## <a name="requirements"></a>要求  
 **标头：** async.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>请参阅  
 [AsyncBase 类](../windows/asyncbase-class.md)