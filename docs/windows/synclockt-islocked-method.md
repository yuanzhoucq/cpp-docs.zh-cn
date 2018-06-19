---
title: 'Synclockt:: Islocked 方法 |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT::IsLocked
dev_langs:
- C++
helpviewer_keywords:
- IsLocked method
ms.assetid: a81fea43-f99a-4708-812a-7fd6af500d3d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 067b3763e10b2bbb310b213f7d748e953ba2a902
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33888470"
---
# <a name="synclocktislocked-method"></a>SyncLockT::IsLocked 方法
支持 WRL 基础结构，不应在代码中直接使用。  
  
## <a name="syntax"></a>语法  
  
```  
bool IsLocked() const;  
```  
  
## <a name="return-value"></a>返回值  
 **true** SyncLockT 对象是否锁定; 否则为**false**。  
  
## <a name="remarks"></a>备注  
 指示当前的 SyncLockT 对象是否拥有资源;SyncLockT 对象也是*锁定*。  
  
## <a name="requirements"></a>要求  
 **标头：** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers::Details  
  
## <a name="see-also"></a>请参阅  
 [SyncLockT 类](../windows/synclockt-class.md)