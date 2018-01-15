---
title: "Semaphore:: operator = 运算符 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::Semaphore::operator=
dev_langs: C++
helpviewer_keywords: operator= operator
ms.assetid: ea19839f-91f0-4b00-a35b-5728fcba4981
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e7608c05c5915a3b4d04cf6a12e1b424e6b44ab4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="semaphoreoperator-operator"></a>Semaphore::operator= 运算符
将指定的句柄从信号量对象移动到当前的信号量对象。  
  
## <a name="syntax"></a>语法  
  
```  
Semaphore& operator=(  
   _Inout_ Semaphore&& h  
);  
```  
  
#### <a name="parameters"></a>参数  
 `h`  
 信号量对象的右值引用。  
  
## <a name="return-value"></a>返回值  
 对当前的信号量对象的引用。  
  
## <a name="requirements"></a>惠?  
 **标头：** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers
 
 ## <a name="see-also"></a>请参阅
 [Semaphore 类](../windows/semaphore-class.md)