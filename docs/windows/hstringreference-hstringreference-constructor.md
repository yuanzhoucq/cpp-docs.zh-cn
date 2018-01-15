---
title: "Hstringreference:: Hstringreference 构造函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::HStringReference::HStringReference
dev_langs: C++
ms.assetid: 29f5fe11-3928-4f60-9861-f0894247bfcb
caps.latest.revision: "2"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 398ea9403f784c30f8e015101c25b071f1d6fb29
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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
  
## <a name="requirements"></a>惠?  
 **标头：** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>请参阅  
 [HStringReference 类](../windows/hstringreference-class.md)