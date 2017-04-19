---
title: '&lt;ostream&gt; typedefs | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ostream/std::ostream
- ostream/std::wostream
ms.assetid: 2ec4dc52-a01f-4654-bd65-dd5288777c48
caps.latest.revision: 11
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 310954b0965be071c288f09de058e3cebe3ce27d
ms.lasthandoff: 02/24/2017

---
# <a name="ltostreamgt-typedefs"></a>&lt;ostream&gt; typedefs
|||  
|-|-|  
|[ostream](#ostream)|[wostream](#wostream)|  
  
##  <a name="ostream"></a>  ostream  
 通过专用于 `char` 的 basic_ostream 和专用于 `char` 的 `char_traits` 创建类型。  
  
```
typedef basic_ostream<char, char_traits<char>> ostream;
```  
  
### <a name="remarks"></a>备注  
 此类型是模板类 [basic_ostream](../standard-library/basic-ostream-class.md) 的同义词，专用于具有默认字符特征的 `char` 类型的元素。  
  
##  <a name="wostream"></a>  wostream  
 通过专用于 `wchar_t` 的 basic_ostream 和专用于 `wchar_t` 的 `char_traits` 创建类型。  
  
```
typedef basic_ostream<wchar_t, char_traits<wchar_t>> wostream;
```  
  
### <a name="remarks"></a>备注  
 此类型是模板类 [basic_ostream](../standard-library/basic-ostream-class.md) 的同义词，专用于具有默认字符特征的 `wchar_t` 类型的元素。  
  
## <a name="see-also"></a>另请参阅  
 [\<ostream>](../standard-library/ostream.md)




