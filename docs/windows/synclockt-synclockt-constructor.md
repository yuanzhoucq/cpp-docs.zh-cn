---
title: 'Synclockt:: Synclockt 构造函数 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT::SyncLockT
dev_langs:
- C++
helpviewer_keywords:
- SyncLockT, constructor
ms.assetid: 713dfd9f-7369-4d86-b4a0-8b32c184d89b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ceaafd6230e6497ed2b7636ad5070141546cb8d6
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39648160"
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
  
### <a name="parameters"></a>参数  
 *other*  
 对另一个右值引用**SyncLockT**对象。  
  
 *sync*  
 对另一个引用`SyncLockWithStatusT`对象。  
  
## <a name="remarks"></a>备注  
 初始化的新实例**SyncLockT**类。  
  
 第一个构造函数初始化当前**SyncLockT**从另一个对象**SyncLockT**对象由参数指定*其他*，并使其他然后无效**SyncLockT**对象。 第二个构造函数是**受保护**，并初始化当前**SyncLockT**为无效状态的对象。  
  
## <a name="requirements"></a>要求  
 **标头：** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers::Details  
  
## <a name="see-also"></a>请参阅  
 [SyncLockT 类](../windows/synclockt-class.md)