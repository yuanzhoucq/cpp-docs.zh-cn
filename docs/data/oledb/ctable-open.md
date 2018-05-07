---
title: 'Ctable:: Open |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.CTable.Open
- ATL::CTable::Open
- CTable::Open
- CTable.Open
dev_langs:
- C++
helpviewer_keywords:
- Open method
ms.assetid: 5d006d95-74d7-4e2b-b243-a33bc53b5455
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ca271d8a88035151e6845db6b7cb9423c71c73ce
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="ctableopen"></a>CTable::Open
打开表。  
  
## <a name="syntax"></a>语法  
  
```cpp
HRESULT Open(const CSession& session,  
   LPCWSTR wszTableName,  
   DBPROPSET* pPropSet = NULL,  
   ULONG ulPropSets = 0) throw ();  


HRESULT Open(const CSession& session,  
   LPCSTR szTableName,  
   DBPROPSET* pPropSet = NULL,  
   ULONG ulPropSets = 0) throw ();  


HRESULT Open(const CSession& session,  
   DBID& dbid,  
   DBPROPSET* pPropSet = NULL,  
   ULONG ulPropSets = 0) throw ();  
```  
  
#### <a name="parameters"></a>参数  
 `session`  
 [in]为其打开表会话。  
  
 *wszTableName*  
 [in]若要打开，表的名称传递为 Unicode 字符串。  
  
 *szTableName*  
 [in]若要打开，表的名称传递为 ANSI 字符串。  
  
 *dbid*  
 [in]**DBID**要打开的表。  
  
 *pPropSet*  
 [in]指向数组的指针[DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx)包含属性和要设置值的结构。 请参阅[属性设置和属性组](https://msdn.microsoft.com/en-us/library/ms713696.aspx)中*OLE DB 程序员参考*Windows SDK 中。 默认值为 NULL 指定任何属性。  
  
 `ulPropSets`  
 [in]数[DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx)结构*pPropSet*自变量。  
  
## <a name="return-value"></a>返回值  
 一个标准 `HRESULT`。  
  
## <a name="remarks"></a>备注  
 有关更多详细信息，请参阅[IOpenRowset::OpenRowset](https://msdn.microsoft.com/en-us/library/ms716724.aspx)中*OLE DB 程序员参考*。  
  
## <a name="requirements"></a>要求  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [CTable 类](../../data/oledb/ctable-class.md)