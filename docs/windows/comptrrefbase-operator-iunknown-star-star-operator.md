---
title: "Comptrrefbase:: Operator IUnknown * * 运算符 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: client/Microsoft::WRL::Details::ComPtrRefBase::operator IUnknown**
dev_langs: C++
helpviewer_keywords: operator IUnknown** operator
ms.assetid: c2950abf-a7aa-480a-ba41-615703e7f931
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 3881dbec0af43f87ff3f880da71299efdf26c64a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="comptrrefbaseoperator-iunknown-operator"></a>ComPtrRefBase::operator IUnknown** 运算符
支持 WRL 基础结构，不应在代码中直接使用。  
  
## <a name="syntax"></a>语法  
  
```  
operator IUnknown**() const;  
```  
  
## <a name="remarks"></a>备注  
 将当前强制转换[ptr_](../windows/comptrrefbase-ptr-data-member.md)对指针到-a-指针-到的数据成员的 IUnknown 接口。  
  
 如果当前 ComPtrRefBase 不派生自 IUnknown，会发出错误。  
  
## <a name="requirements"></a>要求  
 **标头：** client.h  
  
 **Namespace:** Microsoft::WRL::Details  
  
## <a name="see-also"></a>另请参阅  
 [ComPtrRefBase 类](../windows/comptrrefbase-class.md)   
 [Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)