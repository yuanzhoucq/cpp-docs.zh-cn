---
title: 最小值 (STL/CLR) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::min
dev_langs:
- C++
helpviewer_keywords:
- min function [STL/CLR]
ms.assetid: 7a2c82d1-424c-48a9-a944-adcf95511aef
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 5449af49537a2a7633048415d06217edbc64783d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33131954"
---
# <a name="min-stlclr"></a>min (STL/CLR)
比较两个对象并返回较小对象，其中排序条件可通过二元谓词指定。  
  
## <a name="syntax"></a>语法  
  
```  
template<class _Ty> inline  
    const _Ty min(const _Ty% _Left, const _Ty% _Right);  
template<class _Ty, class _Pr> inline  
    const _Ty min(const _Ty% _Left, const _Ty% _Right, _Pr _Pred);  
```  
  
## <a name="remarks"></a>备注  
 此函数的行为与 c + + 标准库函数相同`min`。 有关详细信息，请参阅[min](../standard-library/algorithm-functions.md#min)。  
  
## <a name="requirements"></a>要求  
 **标头：** \<cliext/算法 >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>请参阅  
 [algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)