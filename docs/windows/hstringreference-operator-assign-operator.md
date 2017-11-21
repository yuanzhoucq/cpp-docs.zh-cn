---
title: "Hstringreference:: Operator = 运算符 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::HStringReference::operator=
dev_langs: C++
ms.assetid: ea100ed3-e566-4c9e-b6a8-f296088dea9c
caps.latest.revision: "2"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 2b6a9938308f0cbd8339c24d1876c09ae49df349
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
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
  
## <a name="see-also"></a>另请参阅  
 [HStringReference 类](../windows/hstringreference-class.md)