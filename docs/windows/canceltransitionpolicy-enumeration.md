---
title: "CancelTransitionPolicy 枚举 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::CancelTransitionPolicy::TransitionFromCanceled
- module/Microsoft::WRL::CancelTransitionPolicy::RemainCanceled
- module/Microsoft::WRL::CancelTransitionPolicy
dev_langs: C++
helpviewer_keywords: CancelTransitionPolicy Enumeration
ms.assetid: 5de49f7d-e5e3-43e9-bbca-666caf226cef
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 7f21959daf740155a70787f7c35f8467d1fb2149
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="canceltransitionpolicy-enumeration"></a>CancelTransitionPolicy 枚举
指示如何异步操作的尝试，则切换为终端状态的完成或错误的行为与客户端请求已取消状态。  
  
## <a name="syntax"></a>语法  
  
```  
enum CancelTransitionPolicy;  
```  
  
## <a name="members"></a>成员  
  
### <a name="values"></a>值  
  
|名称|描述|  
|----------|-----------------|  
|`RemainCanceled`|如果异步操作目前在客户端请求已取消状态，这指示它将保持已取消状态而不是转换为已完成的终端或错误状态。|  
|`TransitionFromCanceled`|如果异步操作目前在客户端请求已取消状态，则表明状态应转换到的终端状态的已取消的状态完成从，或使用此标志的调用所根据的错误。|  
  
## <a name="requirements"></a>要求  
 **标头：** async.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>另请参阅  
 [Microsoft::WRL Namespace](../windows/microsoft-wrl-namespace.md)