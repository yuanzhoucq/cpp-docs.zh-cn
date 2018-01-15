---
title: "Asyncbase:: Trytransitiontoerror 方法 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: async/Microsoft::WRL::AsyncBase::TryTransitionToError
dev_langs: C++
helpviewer_keywords: TryTransitionToError method
ms.assetid: f6d11c25-1ce3-43f9-af1c-97c4dc0f6f0f
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6da3d84e3e5e1ee0fd71da1cf59ec79497f81d35
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="asyncbasetrytransitiontoerror-method"></a>AsyncBase::TryTransitionToError 方法
指示指定的错误代码是否可以修改的内部错误状态。  
  
## <a name="syntax"></a>语法  
  
```  
bool TryTransitionToError(  
   const HRESULT error  
);  
```  
  
#### <a name="parameters"></a>参数  
 `error`  
 HRESULT 错误。  
  
## <a name="return-value"></a>返回值  
 `true`如果内部错误状态发生了更改;否则为`false`。  
  
## <a name="remarks"></a>备注  
 此操作修改的错误状态，仅当错误状态已设置为，则为 S_OK。 如果错误状态已为错误，取消、 完成或已关闭，则此操作无效。  
  
## <a name="requirements"></a>惠?  
 **标头：** async.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>请参阅  
 [AsyncBase 类](../windows/asyncbase-class.md)