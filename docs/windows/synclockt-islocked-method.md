---
title: 'Synclockt:: Islocked 方法 |Microsoft Docs'
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
ms.openlocfilehash: c4609866b25f574f34b620d81de3a21d6b608db6
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/09/2018
ms.locfileid: "40020313"
---
# <a name="synclocktislocked-method"></a>SyncLockT::IsLocked 方法
支持 WRL 基础结构，不应在代码中直接使用。  
  
## <a name="syntax"></a>语法  
  
```cpp  
bool IsLocked() const;  
```  
  
## <a name="return-value"></a>返回值  
 **true**如果**SyncLockT**对象是锁定; 否则为**false**。  
  
## <a name="remarks"></a>备注  
 指示是否当前**SyncLockT**对象拥有一个资源; 也就是，则**SyncLockT**对象*锁定*。  
  
## <a name="requirements"></a>要求  
 **标头：** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers::Details  
  
## <a name="see-also"></a>请参阅  
 [SyncLockT 类](../windows/synclockt-class.md)