---
title: "Mutex:: operator = 运算符 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::Mutex::operator=
dev_langs: C++
helpviewer_keywords: operator= operator
ms.assetid: 9b0ee206-a930-4fea-8dc0-1f79839e9d13
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 7b7a9e35bb356d0f3ebfd870105c0b8217d7f658
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="mutexoperator-operator"></a>Mutex::operator= 运算符
分配 （移动） 指定互斥体对象转换为当前的 Mutex 对象。  
  
## <a name="syntax"></a>语法  
  
```  
Mutex& operator=(  
   _Inout_ Mutex&& h  
);  
```  
  
#### <a name="parameters"></a>参数  
 `h`  
 右值引用 Mutex 对象。  
  
## <a name="return-value"></a>返回值  
 对当前的互斥体对象的引用。  
  
## <a name="remarks"></a>备注  
 有关详细信息，请参阅**移动语义**部分[右值引用声明符： & &](../cpp/rvalue-reference-declarator-amp-amp.md)。  
  
## <a name="requirements"></a>要求  
 **标头：** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers
 
 ## <a name="see-also"></a>另请参阅
 [Mutex 类](../windows/mutex-class1.md)