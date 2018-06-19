---
title: 'Semaphore:: operator = 运算符 |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Semaphore::operator=
dev_langs:
- C++
helpviewer_keywords:
- operator= operator
ms.assetid: ea19839f-91f0-4b00-a35b-5728fcba4981
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 25287e642bd368470b207ed237f44ca70773064e
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33892522"
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
  
## <a name="requirements"></a>要求  
 **标头：** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers
 
 ## <a name="see-also"></a>请参阅
 [Semaphore 类](../windows/semaphore-class.md)