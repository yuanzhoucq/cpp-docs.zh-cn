---
title: "Hstringreference:: Operator = = 运算符 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::HStringReference::operator==
dev_langs: C++
ms.assetid: cad3d52d-cd67-4194-a270-5239b1121a09
caps.latest.revision: "2"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 630a10fe751593736fef39d2ca9ba8a56c1d5bed
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="hstringreferenceoperator-operator"></a>HStringReference::Operator== 运算符
指示两个参数是否相等。  
  
## <a name="syntax"></a>语法  
  
```cpp  
inline bool operator==(  
               const HStringReference& lhs,   
               const HStringReference& rhs) throw()  
  
inline bool operator==(  
               const HSTRING& lhs,   
               const HStringReference& rhs) throw()  
  
inline bool operator==(  
               const HStringReference& lhs,   
               const HSTRING& rhs) throw()  
  
```  
  
#### <a name="parameters"></a>参数  
 `lhs`  
 要比较的第一个参数。 `lhs` 可以是 HStringReference 对象或 HSTRING 句柄。  
  
 `rhs`  
 要比较的第二个参数。  `rhs` 可以是 HStringReference 对象或 HSTRING 句柄。  
  
## <a name="return-value"></a>返回值  
 `true`如果`lhs`和`rhs`参数是相等; 否则为`false`。  
  
## <a name="requirements"></a>要求  
 **标头：** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>另请参阅  
 [HStringReference 类](../windows/hstringreference-class.md)