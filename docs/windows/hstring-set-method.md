---
title: 'Hstring:: Set 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString::Set
dev_langs:
- C++
ms.assetid: c9b3d613-95c4-48b0-999d-f5baf0804faf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: aecdafe81dcebc7867d30c46be1fee271e60154c
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2018
ms.locfileid: "39606392"
---
# <a name="hstringset-method"></a>HString::Set 方法
设置的当前值**HString**为指定的宽字符字符串的对象或**HString**参数。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT Set(  
          const wchar_t* str) throw();  
HRESULT Set(   
          const wchar_t* str,   
          unsigned int len  
           ) throw();  
HRESULT Set(  
          const HSTRING& hstr  
           ) throw();  
```  
  
### <a name="parameters"></a>参数  
 *str*  
 宽字符字符串。  
  
 *Len*  
 最大长度*str*分配给当前的参数**HString**对象。  
  
 *hstr*  
 将现有**HString**对象。  
  
## <a name="requirements"></a>要求  
 **标头：** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>请参阅  
 [HString 类](../windows/hstring-class.md)