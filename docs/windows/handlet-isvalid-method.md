---
title: 'Handlet:: Isvalid 方法 |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleT::IsValid
dev_langs:
- C++
helpviewer_keywords:
- IsValid method
ms.assetid: 2c3e72fd-e67b-4908-9929-9007e1a4fc25
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 42aca81b3c2a0ad3db652bf9f77c648e503098e2
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33873129"
---
# <a name="handletisvalid-method"></a>HandleT::IsValid 方法
指示当前 HandleT 对象是否表示句柄。  
  
## <a name="syntax"></a>语法  
  
```  
bool IsValid() const;  
```  
  
## <a name="return-value"></a>返回值  
 如果 HandleT 表示句柄，则为 `true`；否则为 `false`。  
  
## <a name="requirements"></a>要求  
 **标头：** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>请参阅  
 [HandleT 类](../windows/handlet-class.md)