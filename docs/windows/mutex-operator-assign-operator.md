---
title: 'Mutex:: operator = 运算符 |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Mutex::operator=
dev_langs:
- C++
helpviewer_keywords:
- operator= operator
ms.assetid: 9b0ee206-a930-4fea-8dc0-1f79839e9d13
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8791d3c947206be399f475bb8c895b2b5e032133
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33875482"
---
# <a name="mutexoperator-operator"></a>Mutex::operator= 运算符
分配 （移动） 指定互斥体对象转换为当前的 Mutex 对象。  
  
## <a name="syntax"></a>语法  
  
```  
Mutex& operator=(  
   _Inout_ Mutex&& h  
);  
```  
  
#### <a name="parameters"></a>参数  
 `h`  
 右值引用 Mutex 对象。  
  
## <a name="return-value"></a>返回值  
 对当前的互斥体对象的引用。  
  
## <a name="remarks"></a>备注  
 有关详细信息，请参阅**移动语义**部分[右值引用声明符： & &](../cpp/rvalue-reference-declarator-amp-amp.md)。  
  
## <a name="requirements"></a>要求  
 **标头：** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers
 
 ## <a name="see-also"></a>请参阅
 [Mutex 类](../windows/mutex-class1.md)