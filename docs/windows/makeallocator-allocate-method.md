---
title: 'Makeallocator:: Allocate 方法 |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::MakeAllocator::Allocate
dev_langs:
- C++
helpviewer_keywords:
- Allocate method
ms.assetid: a01997bc-4ff1-4ed0-9def-e4aaa15b0598
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d0e8d387dea7687ad61d85f975d58aa47489266d
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="makeallocatorallocate-method"></a>MakeAllocator::Allocate 方法
支持 WRL 基础结构，不应在代码中直接使用。  
  
## <a name="syntax"></a>语法  
  
```  
__forceinline void* Allocate();  
```  
  
## <a name="return-value"></a>返回值  
 如果成功，指向已分配的内存中; 的指针否则为`nullptr`。  
  
## <a name="remarks"></a>备注  
 分配内存并将其与当前的 MakeAllocator 对象关联。  
  
 分配的大小是类型的内存的由当前的 MakeAllocator 模板参数指定的大小。  
  
 开发人员需要重写仅 Allocate() 方法以实现不同的内存分配模型。  
  
## <a name="requirements"></a>要求  
 **标头：** implements.h  
  
 **Namespace:** Microsoft::WRL::Details  
  
## <a name="see-also"></a>请参阅  
 [MakeAllocator 类](../windows/makeallocator-class.md)   
 [Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)