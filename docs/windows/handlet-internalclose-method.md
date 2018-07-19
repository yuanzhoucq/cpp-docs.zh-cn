---
title: 'Handlet:: Internalclose 方法 |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleT::InternalClose
dev_langs:
- C++
helpviewer_keywords:
- InternalClose method
ms.assetid: fe693c02-aa1f-4e00-8bdd-a0d7d736da0b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7b0aef97645d515a03dcf2cab90eedc06f07971c
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33874140"
---
# <a name="handletinternalclose-method"></a>HandleT::InternalClose 方法
关闭当前的 HandleT 对象。  
  
## <a name="syntax"></a>语法  
  
```  
virtual bool InternalClose();  
```  
  
## <a name="return-value"></a>返回值  
 `true` 如果成功，则关闭当前的 HandleT否则为`false`。  
  
## <a name="remarks"></a>备注  
 InternalClose() 进行保护。  
  
## <a name="requirements"></a>要求  
 **标头：** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>请参阅  
 [HandleT 类](../windows/handlet-class.md)