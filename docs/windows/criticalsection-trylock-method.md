---
title: 'Criticalsection:: Trylock 方法 |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection::TryLock
dev_langs:
- C++
helpviewer_keywords:
- TryLock method
ms.assetid: 504bb87c-2cd0-4f54-b458-b3efb9789053
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b4ee99d82212d0d6cdd610b4565bd9292a0265dc
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="criticalsectiontrylock-method"></a>CriticalSection::TryLock 方法
尝试进入临界区而不阻止。 如果调用成功，则调用线程将获得的关键部分所有权。  
  
## <a name="syntax"></a>语法  
  
```  
SyncLock TryLock();  
  
static SyncLock TryLock(  
   _In_ CRITICAL_SECTION* cs  
);  
```  
  
#### <a name="parameters"></a>参数  
 `cs`  
 用户指定的关键部分对象。  
  
## <a name="return-value"></a>返回值  
 如果成功进入临界区的非零值或当前线程已拥有的关键部分。 如果另一个线程已拥有的关键部分，则为零。  
  
## <a name="remarks"></a>备注  
 第一个**TryLock**函数影响当前关键部分对象。 第二个**TryLock**函数影响用户指定的关键部分。  
  
## <a name="requirements"></a>要求  
 **标头：** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>请参阅  
 [CriticalSection 类](../windows/criticalsection-class.md)