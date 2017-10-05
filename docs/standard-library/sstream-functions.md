---
title: "&lt;sstream&gt; 函数 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sstream/std::swap
ms.assetid: bc9607e8-7c6b-44ef-949b-19e917b450ad
caps.latest.revision: 10
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 65f4e356ad0d46333b0d443d0fd6ac0b9f2b6f58
ms.openlocfilehash: dfa71e79d801fbe48f55b81ae4189cdd6d977afe
ms.contentlocale: zh-cn
ms.lasthandoff: 10/03/2017

---
# <a name="ltsstreamgt-functions"></a>&lt;sstream&gt; 函数
||  
|-|  
|[swap](#sstream_swap)|  
  
##  <a name="sstream_swap"></a>swap  
 交换两个 `sstream` 对象间的值。  
  
```  
template <class Elem, class Tr, class Alloc>  
void swap(
    basic_stringbuf<Elem, Tr, Alloc>& left,  
    basic_stringbuf<Elem, Tr, Alloc>& right);

template <class Elem, class Tr, class Alloc>  
void swap(
    basic_istringstream<Elem, Tr, Alloc>& left,  
    basic_istringstream<Elem, Tr, Alloc>& right);

template <class Elem, class Tr, class Alloc>  
void swap(
    basic_ostringstream<Elem, Tr, Alloc>& left,  
    basic_ostringstream<Elem, Tr, Alloc>& right);

template <class Elem, class Tr, class Alloc>  
void swap(
    basic_stringstream<Elem, Tr, Alloc>& left,  
    basic_stringstream<Elem, Tr, Alloc>& right);
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|`left`|引用 `sstream` 对象。|  
|`right`|引用 `sstream` 对象。|  
  
### <a name="remarks"></a>备注  
 该模板函数执行 `left.swap(right)`。  
  
## <a name="see-also"></a>另请参阅  
 [\<sstream>](../standard-library/sstream.md)


