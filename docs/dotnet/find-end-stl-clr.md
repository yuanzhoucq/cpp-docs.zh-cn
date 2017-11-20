---
title: "find_end (STL/CLR) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::find_end
dev_langs: C++
helpviewer_keywords: find_end function [STL/CLR]
ms.assetid: a2008414-163a-4da2-9ac6-4e3c85a02d38
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b7a758c690d1ddb2cda6d6265b6a65c80bd46322
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="findend-stlclr"></a>find_end (STL/CLR)
在范围中查找与指定序列相同的最后一个序列，或在二元谓词指定的意义上等效的最后一个序列。  
  
## <a name="syntax"></a>语法  
  
```  
template<class _FwdIt1, class _FwdIt2> inline  
    _FwdIt1 find_end(_FwdIt1 _First1, _FwdIt1 _Last1,  
        _FwdIt2 _First2, _FwdIt2 _Last2);  
template<class _FwdIt1, class _FwdIt2, class _Pr> inline  
    _FwdIt1 find_end(_FwdIt1 _First1, _FwdIt1 _Last1,  
        _FwdIt2 _First2, _FwdIt2 _Last2, _Pr _Pred);  
```  
  
## <a name="remarks"></a>备注  
 此函数的行为与 c + + 标准库函数相同`find_end`。 有关详细信息，请参阅[find_end](../standard-library/algorithm-functions.md#find_end)。  
  
## <a name="requirements"></a>要求  
 **标头：** \<cliext/算法 >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>另请参阅  
 [algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)