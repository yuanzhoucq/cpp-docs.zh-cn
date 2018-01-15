---
title: "AsyncStatusInternal 枚举 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: async/Microsoft::WRL::Details::AsyncStatusInternal
dev_langs: C++
helpviewer_keywords: AsyncStatusInternal enumeration
ms.assetid: b783923f-3f1c-4487-9384-be572cbc62d7
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: bd277fecb0bc63d5ee823af98df8aa298b285964
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="asyncstatusinternal-enumeration"></a>AsyncStatusInternal 枚举
支持 WRL 基础结构，不应在代码中直接使用。  
  
## <a name="syntax"></a>语法  
  
```  
enum AsyncStatusInternal;  
```  
  
## <a name="remarks"></a>备注  
 指定状态的异步操作的内部枚举之间的映射和**Windows::Foundation::AsyncStatus**枚举。  
  
## <a name="members"></a>成员  
 `_Created`  
 等效于:: Windows::Foundation::AsyncStatus:: 创建  
  
 `_Started`  
 等效于:: Windows::Foundation::AsyncStatus:: 启动  
  
 `_Completed`  
 等效于:: Windows::Foundation::AsyncStatus:: 完成  
  
 `_Cancelled`  
 等效于:: Windows::Foundation::AsyncStatus:: 已取消  
  
 `_Error`  
 等效于:: Windows::Foundation::AsyncStatus::Error  
  
## <a name="requirements"></a>惠?  
 **标头：** async.h  
  
 **Namespace:** Microsoft::WRL::Details  
  
## <a name="see-also"></a>请参阅  
 [Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)