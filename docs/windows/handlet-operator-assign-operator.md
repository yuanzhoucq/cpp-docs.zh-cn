---
title: "Handlet:: Operator = 运算符 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::HandleT::operator=
dev_langs: C++
helpviewer_keywords: operator= operator
ms.assetid: 9e42dcca-30fa-4e8b-8954-802fd64a5595
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5c71e29fa31c89c030b74843a9d776923fed6789
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="handletoperator-operator"></a>HandleT::operator= 运算符
将指定的 HandleT 对象的值移到当前的 HandleT 对象。  
  
## <a name="syntax"></a>语法  
  
```  
HandleT& operator=(  
   _Inout_ HandleT&& h  
);  
```  
  
#### <a name="parameters"></a>参数  
 `h`  
 右值引用的句柄。  
  
## <a name="return-value"></a>返回值  
 对当前的 HandleT 对象的引用。  
  
## <a name="remarks"></a>备注  
 此操作将使失效参数指定的 HandleT 对象`h`。  
  
## <a name="requirements"></a>要求  
 **标头：** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>另请参阅  
 [HandleT 类](../windows/handlet-class.md)