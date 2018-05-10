---
title: 'Handlet:: Detach 方法 |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleT::Detach
dev_langs:
- C++
helpviewer_keywords:
- Detach method
ms.assetid: f7df0f90-fafb-4d1b-a215-a6c62941f6b0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 100d215099494c9b2714fd2c42dee69644a5006c
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="handletdetach-method"></a>HandleT::Detach 方法
解除关联从其基础句柄当前的 HandleT 对象。  
  
## <a name="syntax"></a>语法  
  
```  
typename HandleTraits::Type Detach();  
```  
  
## <a name="return-value"></a>返回值  
 基础句柄。  
  
## <a name="remarks"></a>备注  
 此操作完成后，则会将当前的 HandleT 设置为无效状态。  
  
## <a name="requirements"></a>要求  
 **标头：** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>请参阅  
 [HandleT 类](../windows/handlet-class.md)