---
title: "Comptrref:: Operator T * 运算符 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: client/Microsoft::WRL::Details::ComPtrRef::operator T*
dev_langs: C++
helpviewer_keywords: operator T* operator
ms.assetid: b4f83370-0ebc-4d56-87c6-1a8ea2d0079b
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f69c3680d889006a461e2ee49459c8dcb0020a1c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="comptrrefoperator-t-operator"></a>ComPtrRef::operator T* 运算符
支持 WRL 基础结构，不应在代码中直接使用。  
  
## <a name="syntax"></a>语法  
  
```  
operator T*();  
```  
  
## <a name="remarks"></a>备注  
 返回的值[ptr_](../windows/comptrrefbase-ptr-data-member.md)当前 ComPtrRef 对象的数据成员。  
  
## <a name="requirements"></a>要求  
 **标头：** client.h  
  
 **Namespace:** Microsoft::WRL::Details  
  
## <a name="see-also"></a>另请参阅  
 [ComPtrRef 类](../windows/comptrref-class.md)   
 [Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)