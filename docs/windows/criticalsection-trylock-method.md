---
title: "Criticalsection:: Trylock 方法 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::CriticalSection::TryLock
dev_langs: C++
helpviewer_keywords: TryLock method
ms.assetid: 504bb87c-2cd0-4f54-b458-b3efb9789053
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f2bd717e3a91d2e0210adced36e33a89f3752fa8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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
  
## <a name="requirements"></a>惠?  
 **标头：** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>请参阅  
 [CriticalSection 类](../windows/criticalsection-class.md)