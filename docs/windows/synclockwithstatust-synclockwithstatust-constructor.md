---
title: "Synclockwithstatust:: Synclockwithstatust 构造函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::SyncLockWithStatusT
dev_langs: C++
helpviewer_keywords: SyncLockWithStatusT, constructor
ms.assetid: 5d2fb820-ae1b-495f-8084-ebb4fecc3104
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: dc5be4a37182cb23b47a2511d2e7d5eb0ffa558a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="synclockwithstatustsynclockwithstatust-constructor"></a>SyncLockWithStatusT::SyncLockWithStatusT 构造函数
支持 WRL 基础结构，不应在代码中直接使用。  
  
## <a name="syntax"></a>语法  
  
```  
SyncLockWithStatusT(  
   _Inout_ SyncLockWithStatusT&& other  
);  
  
explicit SyncLockWithStatusT(  
   typename SyncTraits::Type sync,  
   DWORD status  
);  
```  
  
#### <a name="parameters"></a>参数  
 `other`  
 右值引用到另一个 SyncLockWithStatusT 对象。  
  
 `sync`  
 对另一个 SyncLockWithStatusT 对象的引用。  
  
 `status`  
 值[status_](../windows/synclockwithstatust-status-data-member.md)数据成员的`other`参数或`sync`参数。  
  
## <a name="remarks"></a>备注  
 初始化 SyncLockWithStatusT 类的新实例。  
  
 第一个构造函数初始化当前 SyncLockWithStatusT 对象从参数所指定的另一个 SyncLockWithStatusT `other`，然后会与其他 SyncLockWithStatusT 对象。 第二个构造函数是`protected`，并将当前 SyncLockWithStatusT 对象初始化为无效状态。  
  
## <a name="requirements"></a>惠?  
 **标头：** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers::Details  
  
## <a name="see-also"></a>请参阅  
 [SyncLockWithStatusT 类](../windows/synclockwithstatust-class.md)   
 [SyncLockWithStatusT::GetStatus 方法](../windows/synclockwithstatust-getstatus-method.md)