---
title: "Asyncbase:: Start 方法 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: async/Microsoft::WRL::AsyncBase::Start
dev_langs: C++
helpviewer_keywords: Start method
ms.assetid: 67405c9d-0d1a-4c1e-8ea4-6ba01c1f90d9
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 419cbec3500977ec5dbeb063e444c1fced8783aa
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="asyncbasestart-method"></a>AsyncBase::Start 方法
启动异步操作。  
  
## <a name="syntax"></a>语法  
  
```  
STDMETHOD(  
   Start  
)(void);  
```  
  
## <a name="return-value"></a>返回值  
 如果该操作启动或已，启动，则为 S_OK;否则为 E_ILLEGAL_STATE_CHANGE。  
  
## <a name="remarks"></a>备注  
 Start （） IAsyncInfo::Start，默认实现，并且不执行任何实际工作。 若要实际开始一个异步操作，重写 onstart （） 的纯虚方法。  
  
## <a name="requirements"></a>惠?  
 **标头：** async.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>请参阅  
 [AsyncBase 类](../windows/asyncbase-class.md)