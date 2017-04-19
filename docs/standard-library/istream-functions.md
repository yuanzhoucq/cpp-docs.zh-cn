---
title: "&lt;istream&gt; 函数 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- istream/std::swap
- istream/std::ws
ms.assetid: 0301ea0d-4ded-4841-83dd-4253b55b3188
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: aa35f177bcb986e141d0e46e48dc007a96f94498
ms.lasthandoff: 02/24/2017

---
# <a name="ltistreamgt-functions"></a>&lt;istream&gt; 函数
|||  
|-|-|  
|[swap](#istream_swap)|[ws](#ws)|  
  
##  <a name="istream_swap"></a>swap  
 交换两个流对象的元素。  
  
```  
template <class Elem, class Tr>  
void swap(
    basic_istream<Elem, Tr>& left,  
    basic_istream<Elem, Tr>& right);

template <class Elem, class Tr>  
void swap(
    basic_iostream<Elem, Tr>& left,  
    basic_iostream<Elem, Tr>& right);
```  
  
### <a name="parameters"></a>参数  
 `left`  
 一个流。  
  
 `right`  
 一个流。  
  
##  <a name="ws"></a>  ws  
 跳过流中的空白。  
  
```  
template class<Elem, Tr> basic_istream<Elem, Tr>& ws(basic_istream<Elem, Tr>& _Istr);
```  
  
### <a name="parameters"></a>参数  
 `_Istr`  
 一个流。  
  
### <a name="return-value"></a>返回值  
 流。  
  
### <a name="remarks"></a>备注  
 此操控器提取并放弃任何 `ch` 元素，对于这些元素，[use_facet](../standard-library/basic-filebuf-class.md#basic_filebuf__open)< **ctype**\< **Elem**> >( [getloc](../standard-library/ios-base-class.md#ios_base__getloc)). **is**( **ctype**\< **Elem**>:: **space**, **ch**) 为 true。  
  
 此函数如果在提取元素时遇到文件末尾，则会调用 [setstate](../standard-library/basic-ios-class.md#basic_ios__setstate)( **eofbit**)。 它将返回 `_Istr`。  
  
### <a name="example"></a>示例  
  有关使用 `ws` 的示例，请参阅 [operator>>](../standard-library/istream-operators.md#operator_gt__gt_)。  
  
## <a name="see-also"></a>另请参阅  
 [\<istream>](../standard-library/istream.md)


