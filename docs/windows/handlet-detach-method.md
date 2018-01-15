---
title: "Handlet:: Detach 方法 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::HandleT::Detach
dev_langs: C++
helpviewer_keywords: Detach method
ms.assetid: f7df0f90-fafb-4d1b-a215-a6c62941f6b0
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 25ee0e3ea826d77795bbdfafda780071d7a817a6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="handletdetach-method"></a>HandleT::Detach 方法
解除关联从其基础句柄当前的 HandleT 对象。  
  
## <a name="syntax"></a>语法  
  
```  
typename HandleTraits::Type Detach();  
```  
  
## <a name="return-value"></a>返回值  
 基础句柄。  
  
## <a name="remarks"></a>备注  
 此操作完成后，则会将当前的 HandleT 设置为无效状态。  
  
## <a name="requirements"></a>惠?  
 **标头：** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>请参阅  
 [HandleT 类](../windows/handlet-class.md)