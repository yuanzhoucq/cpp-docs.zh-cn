---
title: 'Hstringreference:: Operator = 运算符 |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::operator=
dev_langs:
- C++
ms.assetid: ea100ed3-e566-4c9e-b6a8-f296088dea9c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 73ec71526d340aafb16ddf2af274dce7ad0e9cbd
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33875534"
---
# <a name="hstringreferenceoperator-operator"></a>HStringReference::Operator= 运算符
将另一 HStringReference 对象的值移到当前 HStringReference 对象。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HStringReference& operator=(HStringReference&& other) throw()  
```  
  
#### <a name="parameters"></a>参数  
 `other`  
 现有 HStringReference 对象。  
  
## <a name="remarks"></a>备注  
 现有 `other` 对象的值将复制到当前 HStringReference 对象，然后将销毁 `other` 对象。  
  
## <a name="requirements"></a>要求  
 **标头：** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>请参阅  
 [HStringReference 类](../windows/hstringreference-class.md)