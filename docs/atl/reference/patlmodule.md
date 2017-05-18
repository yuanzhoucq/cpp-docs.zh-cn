---
title: "_pAtlModule |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATLBASE/_pAtlModule
- _pAtlModule
- ATL::_pAtlModule
- ATL._pAtlModule
dev_langs:
- C++
helpviewer_keywords:
- pAtlModule variable
- _pAtlModule variable
ms.assetid: 0ecde3a9-3f4d-4c7b-bb54-713ce05c4777
caps.latest.revision: 13
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5187996fc377bca8633360082d07f7ec8a68ee57
ms.openlocfilehash: b20c5010616323eac9438223df64af9960192e2b
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="patlmodule"></a>_pAtlModule
存储指向当前模块的全局变量。  
  
## <a name="syntax"></a>语法  
  
```  
__declspec(selectany) CAtlModule* _pAtlModule  
```  
  
## <a name="remarks"></a>备注  
 可以使用该全局变量上的方法以提供功能的 （现在已过时） 类[CComModule](../../atl/reference/ccommodule-class.md) Visual c + + 6.0 中提供。  
  
## <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Windowing #&97;](../../atl/codesnippet/cpp/patlmodule_1.cpp)]  
  
## <a name="requirements"></a>要求  
 **标头︰** atlbase.h  
  
## <a name="see-also"></a>另请参阅  
 [全局变量](../../atl/reference/atl-global-variables.md)




