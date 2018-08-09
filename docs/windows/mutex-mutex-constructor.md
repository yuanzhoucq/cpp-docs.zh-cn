---
title: 'Mutex:: mutex 构造函数 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Mutex::Mutex
dev_langs:
- C++
helpviewer_keywords:
- Mutex, constructor
ms.assetid: 504afcdc-775a-4c98-a06f-4fb4663eba3f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d87c07f7fa4f1dfa6cbb34545d74d75e8a867583
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/09/2018
ms.locfileid: "40017079"
---
# <a name="mutexmutex-constructor"></a>Mutex::Mutex 构造函数
初始化的新实例**互斥体**类。  
  
## <a name="syntax"></a>语法  
  
```cpp  
explicit Mutex(  
   HANDLE h  
);  
  
Mutex(  
   _Inout_ Mutex&& h  
);  
```  
  
### <a name="parameters"></a>参数  
 *h*  
 句柄或右值引用的句柄，向**互斥体**对象。  
  
## <a name="remarks"></a>备注  
 第一个构造函数初始化**互斥体**从指定句柄的对象。 第二个构造函数初始化**Mutex**对象从指定句柄，然后将 mutex 的所有权与当前**互斥体**对象。  
  
## <a name="requirements"></a>要求  
 **标头：** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers
 
 ## <a name="see-also"></a>请参阅
 [Mutex 类](../windows/mutex-class1.md)