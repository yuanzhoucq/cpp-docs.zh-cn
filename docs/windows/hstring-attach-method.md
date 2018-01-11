---
title: "Hstring:: Attach 方法 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::HString::Attach
dev_langs: C++
ms.assetid: 69451979-0014-4959-bc5c-1e4ab6fb28e4
caps.latest.revision: "2"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 081b9ad1d3001c74f2b2c096f5f26fe96c413f68
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="hstringattach-method"></a>HString::Attach 方法
将指定的 HString 对象与当前 HString 对象相关联。  
  
## <a name="syntax"></a>语法  
  
```  
  
void Attach(  
       HSTRING hstr  
       ) throw()  
```  
  
#### <a name="parameters"></a>参数  
 `hstr`  
 现有 HString 对象。  
  
## <a name="requirements"></a>惠?  
 **标头：** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>请参阅  
 [HString 类](../windows/hstring-class.md)