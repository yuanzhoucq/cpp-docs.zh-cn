---
title: 旋转 (STL/CLR) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::rotate
dev_langs:
- C++
helpviewer_keywords:
- rotate function [STL/CLR]
ms.assetid: 61dc89a9-a928-4eb3-89d6-2f5927df0f13
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 68d5670f91356bc301b19c254ab43269726a444f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="rotate-stlclr"></a>rotate (STL/CLR)
交换两个相邻范围中的元素。  
  
## <a name="syntax"></a>语法  
  
```  
template<class _FwdIt> inline  
    void rotate(_FwdIt _First, _FwdIt _Mid, _FwdIt _Last);  
```  
  
## <a name="remarks"></a>备注  
 此函数的行为与 c + + 标准库函数相同`rotate`。 有关详细信息，请参阅[旋转](../standard-library/algorithm-functions.md#rotate)。  
  
## <a name="requirements"></a>要求  
 **标头：** \<cliext/算法 >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>请参阅  
 [algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)