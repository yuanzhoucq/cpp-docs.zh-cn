---
title: 'Hstringreference:: Copyto 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: 179d9b14-1ced-4b16-b297-19ca1e92a462
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: fcd27ab7132739987859024270ac6c82be06e590
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2018
ms.locfileid: "39607788"
---
# <a name="hstringreferencecopyto-method"></a>HStringReference::CopyTo 方法
复制当前**HStringReference**到 HSTRING 对象的对象。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT CopyTo(  
   _Out_ HSTRING *str  
   ) const throw();  
```  
  
#### <a name="parameters"></a>参数  
 *str*  
 接收副本的 HSTRING。  
  
## <a name="remarks"></a>备注  
 此方法调用[WindowsDuplicateString](http://msdn.microsoft.com/library/br224634.aspx)函数。  
  
## <a name="requirements"></a>要求  
 **标头：** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>请参阅  
 [HStringReference 类](../windows/hstringreference-class.md)