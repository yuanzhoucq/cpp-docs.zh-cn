---
title: 'Cenumerator:: Getmoniker |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- GetMoniker
- CEnumerator.GetMoniker
- CEnumerator::GetMoniker
- ATL.CEnumerator.GetMoniker
- ATL::CEnumerator::GetMoniker
dev_langs:
- C++
helpviewer_keywords:
- GetMoniker method
ms.assetid: 69a5cf2d-4a94-41dc-812d-bc1661d516d2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5fe2f440d7aad0fd3aca92d6e7de308345dd8f32
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="cenumeratorgetmoniker"></a>CEnumerator::GetMoniker
分析要提取的字符串可以转换为一个名字对象的组件的显示名称。  
  
## <a name="syntax"></a>语法  
  
```cpp
HRESULT GetMoniker(LPMONIKER* ppMoniker) const throw();  


HRESULT GetMoniker(LPMONIKER* ppMoniker,   
   LPCTSTR lpszDisplayName) const throw();  
```  
  
#### <a name="parameters"></a>参数  
 *ppMoniker*  
 [out]标记分析的显示名称 ([cenumeratoraccessor:: M_szparsename](../../data/oledb/cenumeratoraccessor-m-szparsename.md)) 的当前行。  
  
 *lpszDisplayName*  
 [in]要分析的显示名称。  
  
## <a name="return-value"></a>返回值  
 一个标准 `HRESULT`。  
  
## <a name="requirements"></a>要求  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [CEnumerator 类](../../data/oledb/cenumerator-class.md)