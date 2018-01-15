---
title: "Classfactory:: Lockserver 方法 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: module/Microsoft::WRL::ClassFactory::LockServer
dev_langs: C++
helpviewer_keywords: LockServer method
ms.assetid: 8d859815-956d-4f81-a5af-7cdee7e945de
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5f646f198d884e677b622a312cfdb6187802e1c6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="classfactorylockserver-method"></a>ClassFactory::LockServer 方法
递增或递减当前 ClassFactory 对象跟踪的基础对象数量。  
  
## <a name="syntax"></a>语法  
  
```  
STDMETHOD(  
   LockServer  
)(BOOL fLock);  
```  
  
#### <a name="parameters"></a>参数  
 `fLock`  
 若要递增跟踪对象的数量，则为 `true`。 若要递减跟踪对象的数量，则为 `false`。  
  
## <a name="return-value"></a>返回值  
 如果成功，则为 S_OK；否则为 E_FAIL。  
  
## <a name="remarks"></a>备注  
 ClassFactory 将跟踪的基础实例中的对象[模块](../windows/module-class.md)类。  
  
## <a name="requirements"></a>惠?  
 **标头：** module.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>请参阅  
 [ClassFactory 类](../windows/classfactory-class.md)