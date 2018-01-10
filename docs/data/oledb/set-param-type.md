---
title: "SET_PARAM_TYPE |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SET_PARAM_TYPE
dev_langs: C++
helpviewer_keywords: SET_PARAM_TYPE macro
ms.assetid: 85979070-2d55-4c67-94b1-9b9058babc59
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 024cf67033cdc35917f37c2e6183e60042c40d45
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="setparamtype"></a>SET_PARAM_TYPE
指定将遵循 `COLUMN_ENTRY` 宏输入、输出或输入/输出的 `SET_PARAM_TYPE` 。  
  
## <a name="syntax"></a>语法  
  
```  
  
SET_PARAM_TYPE(  
type  
 )  
  
```  
  
#### <a name="parameters"></a>参数  
 `type`  
 [in] 要为参数设置的类型。  
  
## <a name="remarks"></a>备注  
 提供程序仅支持基础数据源支持的参数输入/输出类型。 类型是一个或多个 **DBPARAMIO** 值的组合（请参阅 [OLE DB 程序员参考](https://msdn.microsoft.com/en-us/library/ms716845.aspx) 中的 *DBBINDING 结构*）：  
  
-   **DBPARAMIO_NOTPARAM** 访问器没有参数。 通常，将 **eParamIO** 设置为行访问器中的此值以提醒用户将忽略参数。  
  
-   **DBPARAMIO_INPUT** 输入参数。  
  
-   **DBPARAMIO_OUTPUT** 输出参数。  
  
-   **DBPARAMIO_INPUT &#124;DBPARAMIO_OUTPUT**参数是输入和输出参数。  
  
## <a name="example"></a>示例  
```cpp  
class CArtistsProperty
{
public:
   short m_nReturn;
   short m_nAge;
   TCHAR m_szFirstName[21];
   TCHAR m_szLastName[31];

BEGIN_PARAM_MAP(CArtistsProperty)
   SET_PARAM_TYPE(DBPARAMIO_OUTPUT)
   COLUMN_ENTRY(1, m_nReturn)
   SET_PARAM_TYPE(DBPARAMIO_INPUT)
   COLUMN_ENTRY(2, m_nAge)
END_PARAM_MAP()

BEGIN_COLUMN_MAP(CArtistsProperty)
   COLUMN_ENTRY(1, m_szFirstName)
   COLUMN_ENTRY(2, m_szLastName)
END_COLUMN_MAP()

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

   DEFINE_COMMAND_EX(CArtistsProperty, L" \
      { ? = SELECT Age FROM Artists WHERE Age < ? }")
};
``` 
  
## <a name="requirements"></a>惠?  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [OLE DB 使用者模板的宏和全局函数](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)