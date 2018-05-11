---
title: 'Hstring:: Getaddressof 方法 |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString::GetAddressOf
dev_langs:
- C++
ms.assetid: 6050decf-5f99-49f0-9497-1c8192c485ae
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7d4804373045d12c2e251e2de61b7aefd52ec916
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="hstringgetaddressof-method"></a>HString::GetAddressOf 方法
检索指向基础 HSTRING 句柄的指针。  
  
## <a name="syntax"></a>语法  
  
```  
HSTRING* GetAddressOf() throw()  
```  
  
## <a name="return-value"></a>返回值  
 指向基础 HSTRING 句柄的指针。  
  
## <a name="remarks"></a>备注  
 此操作后，将销毁基础 HSTRING 句柄的字符串值。  
  
## <a name="requirements"></a>要求  
 **标头：** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>请参阅  
 [HString 类](../windows/hstring-class.md)