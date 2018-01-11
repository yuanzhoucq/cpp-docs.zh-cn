---
title: '&lt;ostream&gt; typedefs | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- iosfwd/std::ostream
- iosfwd/std::wostream
ms.assetid: 2ec4dc52-a01f-4654-bd65-dd5288777c48
caps.latest.revision: "11"
manager: ghogen
ms.openlocfilehash: bcf7df720a9b3a71ddbb32bd6eeb73f2f1332391
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
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
  
## <a name="see-also"></a>请参阅  
 [\<ostream>](../standard-library/ostream.md)



