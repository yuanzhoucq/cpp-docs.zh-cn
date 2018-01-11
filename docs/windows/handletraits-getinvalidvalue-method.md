---
title: "Handletraits:: Getinvalidvalue 方法 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLETraits::GetInvalidValue
dev_langs: C++
helpviewer_keywords: GetInvalidValue method
ms.assetid: e95d2cc1-e70f-463f-8ff0-183cdeac1138
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ae903934d3f4002a416d382537185e9927405ea8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="handletraitsgetinvalidvalue-method"></a>HANDLETraits::GetInvalidValue 方法
表示一个无效句柄。  
  
## <a name="syntax"></a>语法  
  
```  
inline static HANDLE GetInvalidValue();  
```  
  
## <a name="return-value"></a>返回值  
 始终返回 INVALID_HANDLE_VALUE。 （INVALID_HANDLE_VALUE 定义由 Windows 中）。  
  
## <a name="requirements"></a>惠?  
 **标头：** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers::HandleTraits  
  
## <a name="see-also"></a>请参阅  
 [HANDLETraits 结构](../windows/handletraits-structure.md)