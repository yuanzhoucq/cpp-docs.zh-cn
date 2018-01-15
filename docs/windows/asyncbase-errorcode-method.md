---
title: "Asyncbase:: Errorcode 方法 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: async/Microsoft::WRL::AsyncBase::ErrorCode
dev_langs: C++
helpviewer_keywords: ErrorCode method
ms.assetid: 3f5f0f69-d60a-4a67-8cc6-a55fdc89a192
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a2f94e3d62e6fb556246877a647ccdc97a47ef2d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="asyncbaseerrorcode-method"></a>AsyncBase::ErrorCode 方法
检索当前的异步操作的错误代码。  
  
## <a name="syntax"></a>语法  
  
```  
inline void ErrorCode(  
   HRESULT *error  
);  
```  
  
#### <a name="parameters"></a>参数  
 `error`  
 此操作存储的当前错误代码的位置。  
  
## <a name="remarks"></a>备注  
 此操作是线程安全的。  
  
## <a name="requirements"></a>惠?  
 **标头：** async.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>请参阅  
 [AsyncBase 类](../windows/asyncbase-class.md)