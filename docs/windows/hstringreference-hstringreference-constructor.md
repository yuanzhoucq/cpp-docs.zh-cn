---
title: 'Hstringreference:: Hstringreference 构造函数 |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::HStringReference
dev_langs:
- C++
ms.assetid: 29f5fe11-3928-4f60-9861-f0894247bfcb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: dc88ea32d4384b36559a4a10da0a5975345bf0d7
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33876002"
---
# <a name="hstringreferencehstringreference-constructor"></a>HStringReference::HStringReference 构造函数
初始化 HStringReference 类的新实例。  
  
## <a name="syntax"></a>语法  
  
```cpp  
template<unsigned int sizeDest>  
HStringReference(wchar_t const (&str)[ sizeDest]) throw();  
  
template<unsigned int sizeDest>  
HStringReference(wchar_t const (&str)[ sizeDest],   
                 unsigned int len) throw();  
  
HStringReference(HStringReference&& other) throw();  
```  
  
#### <a name="parameters"></a>参数  
 `sizeDest`  
 指定目标 HStringReference 缓冲区大小的模板参数。  
  
 `str`  
 对宽字符串的引用。  
  
 `len`  
 要在此操作中使用的 `str` 参数缓冲区的最大长度。 如果 `len` 参数未指定，则将使用整个 `str` 参数。 如果 `len` 大于 `sizeDest`，则 `len` 将设置为 `sizeDest`-1。  
  
 `other`  
 另一 HStringReference 对象。  
  
## <a name="remarks"></a>备注  
 第一个构造函数初始化大小与参数 `str` 相同的新的 HStringReference 对象。  
  
 第二个构造函数初始化大小由参数 `len` 指定的新的 HStringReference 对象。  
  
 第三个构造函数初始化新的 HStringReference 对象的值`other`参数，然后销毁`other`参数。  
  
## <a name="requirements"></a>要求  
 **标头：** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>请参阅  
 [HStringReference 类](../windows/hstringreference-class.md)