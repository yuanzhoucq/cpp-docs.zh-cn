---
title: "Handlet:: Internalclose 方法 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::HandleT::InternalClose
dev_langs: C++
helpviewer_keywords: InternalClose method
ms.assetid: fe693c02-aa1f-4e00-8bdd-a0d7d736da0b
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c91d3a6eb2c03b70ca50b28189e4ab4530a2e3bc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="handletinternalclose-method"></a>HandleT::InternalClose 方法
关闭当前的 HandleT 对象。  
  
## <a name="syntax"></a>语法  
  
```  
virtual bool InternalClose();  
```  
  
## <a name="return-value"></a>返回值  
 `true`如果成功，则关闭当前的 HandleT否则为`false`。  
  
## <a name="remarks"></a>备注  
 InternalClose() 进行保护。  
  
## <a name="requirements"></a>惠?  
 **标头：** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>请参阅  
 [HandleT 类](../windows/handlet-class.md)