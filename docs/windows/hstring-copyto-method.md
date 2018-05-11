---
title: 'Hstring:: Copyto 方法 |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: a1fd2ef0-e175-4c18-927b-550e02a89e43
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b44974faf5fc1f068d28d7febe3ed2a266f4869e
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="hstringcopyto-method"></a>HString::CopyTo 方法
复制当前 HString 对象 HSTRING 对象。  
  
## <a name="syntax"></a>语法  
  
```  
  
HRESULT CopyTo(  
   _Out_ HSTRING *str  
   ) const throw();  
```  
  
#### <a name="parameters"></a>参数  
 `str`  
 HSTRING 接收复制。  
  
## <a name="remarks"></a>备注  
 此方法调用[WindowsDuplicateString](http://msdn.microsoft.com/library/br224634.aspx)函数。  
  
## <a name="requirements"></a>要求  
 **标头：** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>请参阅  
 [HString 类](../windows/hstring-class.md)