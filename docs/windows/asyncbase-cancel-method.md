---
title: "Asyncbase:: Cancel 方法 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: async/Microsoft::WRL::AsyncBase::Cancel
dev_langs: C++
helpviewer_keywords: Cancel method
ms.assetid: 8bfebc63-3848-4629-bc89-aa538ed7e7ad
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5b6215c871da92087a7555bfb5a97f48d60223de
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="asyncbasecancel-method"></a>AsyncBase::Cancel 方法
取消异步操作。  
  
## <a name="syntax"></a>语法  
  
```  
STDMETHOD(  
   Cancel  
)(void);  
```  
  
## <a name="return-value"></a>返回值  
 默认情况下，始终返回，则为 S_OK。  
  
## <a name="remarks"></a>备注  
 Cancel （） IAsyncInfo::Cancel，默认实现，并且不执行任何实际工作。 若要实际取消异步操作，重写 OnCancel() 纯虚方法。  
  
## <a name="requirements"></a>要求  
 **标头：** async.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>另请参阅  
 [AsyncBase 类](../windows/asyncbase-class.md)