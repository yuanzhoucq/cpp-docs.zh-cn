---
title: 'Cenumerator:: Open |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.CEnumerator.Open
- CEnumerator::Open
- ATL::CEnumerator::Open
- CEnumerator.Open
dev_langs:
- C++
helpviewer_keywords:
- Open method
ms.assetid: b22821a0-257a-4543-ad0c-2649d4ac092e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 04e6884b27f45ee86085c1b820376ed087ae68c5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33096920"
---
# <a name="cenumeratoropen"></a>CEnumerator::Open
将名字对象绑定枚举器，如果其中一个指定，则通过调用检索枚举器的行集[ISourcesRowset::GetSourcesRowset](https://msdn.microsoft.com/en-us/library/ms711200.aspx)。  
  
## <a name="syntax"></a>语法  
  
```cpp
HRESULT Open(LPMONIKER pMoniker) throw();  


HRESULT Open(const CLSID* pClsid = & CLSID_OLEDB_ENUMERATOR) throw();  


HRESULT Open(const CEnumerator& enumerator) throw();  
```  
  
#### <a name="parameters"></a>参数  
 `pMoniker`  
 [in]指向一个枚举器的名字对象的指针。  
  
 *pClsid*  
 [in]指向的指针**CLSID**的枚举数。  
  
 `enumerator`  
 [in]对一个枚举器的引用。  
  
## <a name="return-value"></a>返回值  
 一个标准 `HRESULT`。  
  
## <a name="requirements"></a>要求  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [CEnumerator 类](../../data/oledb/cenumerator-class.md)