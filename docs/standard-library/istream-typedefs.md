---
title: '&lt;istream&gt; typedef | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- istream/std::iostream
- istream/std::istream
- istream/std::wiostream
- istream/std::wistream
ms.assetid: 55bc1f84-53a7-46ca-a36f-ac6ef75d0374
caps.latest.revision: 10
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: e3607735f989b61f373eb689b8fe3b2dee656f7b
ms.lasthandoff: 02/24/2017

---
# <a name="ltistreamgt-typedefs"></a>&lt;istream&gt; typedef
||||  
|-|-|-|  
|[iostream](#iostream)|[istream](#istream)|[wiostream](#wiostream)|  
|[wistream](#wistream)|  
  
##  <a name="iostream"></a>iostream  
 专用于 `char` 的类型 `basic_iostream`。  
  
```  
typedef basic_iostream<char, char_traits<char>> iostream;  
```  
  
### <a name="remarks"></a>备注  
 此类型是模板类 [basic_iostream](../standard-library/basic-iostream-class.md) 的同义词，专用于具有默认字符特征的 `char` 类型的元素。  
  
##  <a name="istream"></a>istream  
 专用于 `char` 的类型 `basic_istream`。  
  
```  
typedef basic_istream<char, char_traits<char>> istream;  
```  
  
### <a name="remarks"></a>备注  
 此类型是模板类 [basic_istream](../standard-library/basic-istream-class.md) 的同义词，专用于具有默认字符特征的 `char` 类型的元素。  
  
##  <a name="wiostream"></a>wiostream  
 专用于 `wchar_t` 的类型 `basic_iostream`。  
  
```  
typedef basic_iostream<wchar_t, char_traits<wchar_t>> wiostream;  
```  
  
### <a name="remarks"></a>备注  
 此类型是模板类 [basic_iostream](../standard-library/basic-iostream-class.md) 的同义词，专用于具有默认字符特征的 `wchar_t` 类型的元素。  
  
##  <a name="wistream"></a> wistream  
 专用于 `wchar_t` 的类型 `basic_istream`。  
  
```  
typedef basic_istream<wchar_t, char_traits<wchar_t>> wistream;  
```  
  
### <a name="remarks"></a>备注  
 此类型是模板类 [basic_istream](../standard-library/basic-istream-class.md) 的同义词，专用于具有默认字符特征的 `wchar_t` 类型的元素。  
  
## <a name="see-also"></a>另请参阅  
 [\<istream>](../standard-library/istream.md)


