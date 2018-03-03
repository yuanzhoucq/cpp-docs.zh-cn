---
title: "Synclockt:: Synclockt 构造函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT::SyncLockT
dev_langs:
- C++
helpviewer_keywords:
- SyncLockT, constructor
ms.assetid: 713dfd9f-7369-4d86-b4a0-8b32c184d89b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9e2aa229b85c0d3e40b5f3736c9e5da451102775
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="synclocktsynclockt-constructor"></a>SyncLockT::SyncLockT 构造函数
支持 WRL 基础结构，不应在代码中直接使用。  
  
## <a name="syntax"></a>语法  
  
```  
SyncLockT(  
   _Inout_ SyncLockT&& other  
);  
  
explicit SyncLockT(  
   typename SyncTraits::Type sync = SyncTraits::GetInvalidValue()  
);  
```  
  
#### <a name="parameters"></a>参数  
 `other`  
 右值引用到另一个 SyncLockT 对象。  
  
 `sync`  
 对另一个 SyncLockWithStatusT 对象的引用。  
  
## <a name="remarks"></a>备注  
 初始化 SyncLockT 类的新实例。  
  
 第一个构造函数初始化参数指定的另一个 SyncLockT 对象中的当前 SyncLockT 对象`other`，然后会与其他 SyncLockT 对象。 第二个构造函数是`protected`，并将当前 SyncLockT 对象初始化为无效状态。  
  
## <a name="requirements"></a>惠?  
 **标头：** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers::Details  
  
## <a name="see-also"></a>请参阅  
 [SyncLockT 类](../windows/synclockt-class.md)