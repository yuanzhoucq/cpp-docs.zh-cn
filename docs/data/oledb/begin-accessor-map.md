---
title: BEGIN_ACCESSOR_MAP | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- BEGIN_ACCESSOR_MAP
dev_langs:
- C++
helpviewer_keywords:
- BEGIN_ACCESSOR_MAP macro
ms.assetid: e6d6e3a4-62fa-4e49-8c53-caf8c9d20091
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 0fd9684d3ab428ffa2e874f781208812d1ad12fc
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="beginaccessormap"></a>BEGIN_ACCESSOR_MAP
标记取值函数映射条目的开始。  
  
## <a name="syntax"></a>语法  
  
```  
BEGIN_ACCESSOR_MAP(x, num)  
```  
  
#### <a name="parameters"></a>参数  
 *x*  
 [in] 用户记录类的名称。  
  
 *num*  
 [in] 此取值函数映射中的取值函数数目。  
  
## <a name="remarks"></a>备注  
 如果某个行集上有多个取值函数，则需要在开头指定 `BEGIN_ACCESSOR_MAP` 并对每个单独的取值函数使用 `BEGIN_ACCESSOR` 宏。 `BEGIN_ACCESSOR` 宏以 `END_ACCESSOR` 宏结束。 取值函数映射以 `END_ACCESSOR_MAP` 宏结束。  
  
 如果在用户记录中只有一个取值函数，则使用宏 [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)。  
  
## <a name="example"></a>示例  

 ```cpp  
class CArtistsAccessor
{
public:
// Data Elements
   TCHAR m_szFirstName[21];
   TCHAR m_szLastName[31];
   short m_nAge;

// Output binding map
BEGIN_ACCESSOR_MAP(CArtistsAccessor, 2)
   BEGIN_ACCESSOR(0, true)
      COLUMN_ENTRY(1, m_szFirstName)
      COLUMN_ENTRY(2, m_szLastName)
   END_ACCESSOR()
   BEGIN_ACCESSOR(1, false) // Not an auto accessor
      COLUMN_ENTRY(3, m_nAge)
   END_ACCESSOR()
END_ACCESSOR_MAP()

   HRESULT OpenDataSource()
   {
      CDataSource _db;
      _db.Open();
      return m_session.Open(_db);
   }

   void CloseDataSource()
   {
      m_session.Close();
   }

   CSession m_session;

   DEFINE_COMMAND_EX(CArtistsAccessor, L" \
   SELECT \
      FirstName, \
      LastName, \
      Age \
      FROM Artists")
};
 ```

  
## <a name="requirements"></a>惠?  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [宏和全局函数 OLE DB 使用者模板](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)   
 [END_ACCESSOR](../../data/oledb/end-accessor.md)   
 [END_ACCESSOR_MAP](../../data/oledb/end-accessor-map.md)