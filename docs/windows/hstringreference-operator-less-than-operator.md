---
title: "Hstringreference:: Operator&lt;运算符 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::HStringReference::operator<
dev_langs: C++
ms.assetid: 55aa48e8-7c96-4123-9ebe-42b4cd8b9377
caps.latest.revision: "2"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ac370a8d863e7c71dcd3564b3a5d0ae7d214322d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="hstringreferenceoperatorlt-operator"></a>Hstringreference:: Operator&lt;运算符
指示第一个参数是否小于第二个参数。  
  
## <a name="syntax"></a>语法  
  
```cpp  
inline bool operator<(  
    const HStringReference& lhs,   
    const HStringReference& rhs) throw()  
```  
  
#### <a name="parameters"></a>参数  
 `lhs`  
 要比较的第一个参数。 `lhs`可以是 HStringReference 的引用。  
  
 `rhs`  
 要比较的第二个参数。  `rhs`可以是 HStringReference 的引用。  
  
## <a name="return-value"></a>返回值  
 `true`如果`lhs`参数是小于`rhs`参数; 否则为`false`。  
  
## <a name="requirements"></a>惠?  
 **标头：** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>请参阅  
 [HStringReference 类](../windows/hstringreference-class.md)