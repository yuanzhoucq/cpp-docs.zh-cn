---
title: "Mutex:: mutex 构造函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::Mutex::Mutex
dev_langs: C++
helpviewer_keywords: Mutex, constructor
ms.assetid: 504afcdc-775a-4c98-a06f-4fb4663eba3f
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a07aeac0f8d139f71bdbe2473dc8eabf7e14ec2f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="mutexmutex-constructor"></a>Mutex::Mutex 构造函数
初始化 Mutex 类的新实例。  
  
## <a name="syntax"></a>语法  
  
```  
explicit Mutex(  
   HANDLE h  
);  
  
Mutex(  
   _Inout_ Mutex&& h  
);  
```  
  
#### <a name="parameters"></a>参数  
 `h`  
 Mutex 对象的句柄，或对 Mutex 对象句柄的 rvalue 引用。  
  
## <a name="remarks"></a>备注  
 第一个构造函数通过指定句柄初始化 Mutex 对象。 第二个构造函数通过指定句柄初始化 Mutex 对象，然后将 mutex 的所有权移至当前 Mutex 对象。  
  
## <a name="requirements"></a>惠?  
 **标头：** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers
 
 ## <a name="see-also"></a>请参阅
 [Mutex 类](../windows/mutex-class1.md)