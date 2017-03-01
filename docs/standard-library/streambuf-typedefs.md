---
title: '&lt;streambuf&gt; typedef | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2678e18f-f0f0-4995-bc53-f1bc7dfc4ec6
caps.latest.revision: 11
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 8a11f21fc55babc7c71bb312bc582719f532347a
ms.lasthandoff: 02/24/2017

---
# <a name="ltstreambufgt-typedefs"></a>&lt;streambuf&gt; typedef
|||  
|-|-|  
|[streambuf](#streambuf)|[wstreambuf](#wstreambuf)|  
  
##  <a name="a-namestreambufa--streambuf"></a><a name="streambuf"></a>  streambuf  
 专用化使用 `char` 作为模板参数的 `basic_streambuf`。  
  
```
typedef basic_streambuf<char, char_traits<char>> streambuf;
```  
  
### <a name="remarks"></a>备注  
 该类型是模板类 [basic_streambuf`char` 的同义词，专门用于具有默认字符特征的 ](../standard-library/basic-streambuf-class.md) 类型的元素。  
  
##  <a name="a-namewstreambufa--wstreambuf"></a><a name="wstreambuf"></a>  wstreambuf  
 专用化使用 `wchar_t` 作为模板参数的 `basic_streambuf`。  
  
```
typedef basic_streambuf<wchar_t, char_traits<wchar_t>> wstreambuf;
```  
  
### <a name="remarks"></a>备注  
 该类型是模板类 [basic_streambuf`wchar_t` 的同义词，专门用于具有默认字符特征的 ](../standard-library/basic-streambuf-class.md) 类型的元素。  
  
## <a name="see-also"></a>另请参阅  
 [\<streambuf>](../standard-library/streambuf.md)




