---
title: "Comptrref:: Operator void * * 运算符 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: client/Microsoft::WRL::Details::ComPtrRef::operator void**
dev_langs: C++
helpviewer_keywords: operator void** operator
ms.assetid: f020045c-9de4-4392-8783-73f0fc0761c6
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6f961328444d49bb282b87b4d4670aeab7fe7997
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="comptrrefoperator-void-operator"></a>ComPtrRef::operator void** 运算符
支持 WRL 基础结构，不应在代码中直接使用。  
  
## <a name="syntax"></a>语法  
  
```  
operator void**() const;  
```  
  
## <a name="remarks"></a>备注  
 删除当前 ComPtrRef 对象，作为指针-到-指针-到由 ComPtrRef 对象表示的接口的指针转换`void`，然后返回强制转换指针。  
  
## <a name="requirements"></a>要求  
 **标头：** client.h  
  
 **Namespace:** Microsoft::WRL::Details  
  
## <a name="see-also"></a>另请参阅  
 [ComPtrRef 类](../windows/comptrref-class.md)   
 [Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)