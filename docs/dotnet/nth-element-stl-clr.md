---
title: "nth_element (STL/CLR) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::nth_element
dev_langs: C++
helpviewer_keywords: nth_element function [STL/CLR]
ms.assetid: 19fc1695-62a9-4f85-9920-d153c1c6481f
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e0dc54dda65163f5682b2ee20e5e0b08a63acbd9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="nthelement-stlclr"></a>nth_element (STL/CLR)
分区元素，正确找到范围`n`th 元素的范围中的序列以便前面遮挡它的所有元素都均小于或等于它以及按照序列中的所有元素都是大于或等于它。  
  
## <a name="syntax"></a>语法  
  
```  
template<class _RanIt> inline  
    void nth_element(_RanIt _First, _RanIt _Nth, _RanIt _Last);  
template<class _RanIt, class _Pr> inline  
    void nth_element(_RanIt _First, _RanIt _Nth, _RanIt _Last,  
        _Pr _Pred);  
```  
  
## <a name="remarks"></a>备注  
 此函数的行为与 c + + 标准库函数相同`nth_element`。 有关详细信息，请参阅[nth_element](../standard-library/algorithm-functions.md#nth_element)。  
  
## <a name="requirements"></a>要求  
 **标头：** \<cliext/算法 >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>另请参阅  
 [algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)