---
title: "动态确定返回给使用者的列 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "书签 [C++], 动态确定列"
  - "动态确定列 [C++]"
ms.assetid: 58522b7a-894e-4b7d-a605-f80e900a7f5f
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 动态确定返回给使用者的列
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

PROVIDER\_COLUMN\_ENTRY 宏通常处理 **IColumnsInfo::GetColumnsInfo** 调用。  但是，由于使用者可能选择使用书签，因此提供程序必须能够根据使用者是否要求书签来更改返回的列。  
  
 若要处理 **IColumnsInfo::GetColumnsInfo** 调用，请从 MyProviderRS.h 中的 `CAgentMan` 用户记录中删除 PROVIDER\_COLUMN\_MAP（它定义函数 `GetColumnInfo`），并用自己的 `GetColumnInfo` 函数定义替换它：  
  
```  
////////////////////////////////////////////////////////////////////////  
// MyProviderRS.H  
class CAgentMan  
{  
public:  
   DWORD dwBookmark;  
   TCHAR szCommand[256];  
   TCHAR szText[256];  
   TCHAR szCommand2[256];  
   TCHAR szText2[256];  
  
   static ATLCOLUMNINFO* GetColumnInfo(void* pThis, ULONG* pcCols);  
   bool operator==(const CAgentMan& am)  
   {  
      return (lstrcmpi(szCommand, am.szCommand) == 0);  
   }  
  
};  
```  
  
 下一步，在 MyProviderRS.cpp 中实现 `GetColumnInfo` 函数，如以下代码所示。  
  
 `GetColumnInfo` 首先检查 OLE DB 属性 **DBPROP\_BOOKMARKS** 是否已设置。  为获取该属性，`GetColumnInfo` 使用指向行集合对象的指针 \(`pRowset`\)。  `pThis` 指针表示创建行集合的类，它是存储属性映射的类。  `GetColumnInfo` 将 `pThis` 指针的类型转换为 `RMyProviderRowset` 指针。  
  
 为了检查 DBPROP\_BOOKMARKS属性，`GetColumnInfo` 将使用 `IRowsetInfo` 接口，您可以通过在 `pRowset` 接口上调用 `QueryInterface` 来获取该接口。  另一种选择是，可以改用 ATL [CComQIPtr](../../atl/reference/ccomqiptr-class.md) 方法。  
  
```  
////////////////////////////////////////////////////////////////////  
// MyProviderRS.cpp  
ATLCOLUMNINFO* CAgentMan::GetColumnInfo(void* pThis, ULONG* pcCols)  
{  
   static ATLCOLUMNINFO _rgColumns[5];  
   ULONG ulCols = 0;  
  
   // Check the property flag for bookmarks; if it is set, set the zero   
   // ordinal entry in the column map with the bookmark information.  
   CAgentRowset* pRowset = (CAgentRowset*) pThis;  
   CComQIPtr<IRowsetInfo, &IID_IRowsetInfo> spRowsetProps = pRowset;  
  
   CDBPropIDSet set(DBPROPSET_ROWSET);  
   set.AddPropertyID(DBPROP_BOOKMARKS);  
   DBPROPSET* pPropSet = NULL;  
   ULONG ulPropSet = 0;  
   HRESULT hr;  
  
   if (spRowsetProps)  
      hr = spRowsetProps->GetProperties(1, &set, &ulPropSet, &pPropSet);  
  
   if (pPropSet)  
   {  
      CComVariant var = pPropSet->rgProperties[0].vValue;  
      CoTaskMemFree(pPropSet->rgProperties);  
      CoTaskMemFree(pPropSet);  
  
      if (SUCCEEDED(hr) && (var.boolVal == VARIANT_TRUE))  
      {  
         ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Bookmark"), 0, sizeof(DWORD),   
         DBTYPE_BYTES, 0, 0, GUID_NULL, CAgentMan, dwBookmark,   
         DBCOLUMNFLAGS_ISBOOKMARK)  
         ulCols++;  
      }  
   }  
  
   // Next, set the other columns up.  
   ADD_COLUMN_ENTRY(ulCols, OLESTR("Command"), 1, 256, DBTYPE_STR, 0xFF, 0xFF,   
      GUID_NULL, CAgentMan, szCommand)  
   ulCols++;  
   ADD_COLUMN_ENTRY(ulCols, OLESTR("Text"), 2, 256, DBTYPE_STR, 0xFF, 0xFF,   
      GUID_NULL, CAgentMan, szText)  
   ulCols++;  
  
   ADD_COLUMN_ENTRY(ulCols, OLESTR("Command2"), 3, 256, DBTYPE_STR, 0xFF, 0xFF,   
      GUID_NULL, CAgentMan, szCommand2)  
   ulCols++;  
   ADD_COLUMN_ENTRY(ulCols, OLESTR("Text2"), 4, 256, DBTYPE_STR, 0xFF, 0xFF,   
      GUID_NULL, CAgentMan, szText2)  
   ulCols++;  
  
   if (pcCols != NULL)  
      *pcCols = ulCols;  
  
   return _rgColumns;  
}  
```  
  
 本例使用静态数组包含列信息。  如果使用者不想要书签列，数组中的某一项不使用。  为处理该信息，创建两个数组宏：ADD\_COLUMN\_ENTRY 和 ADD\_COLUMN\_ENTRY\_EX。  ADD\_COLUMN\_ENTRY\_EX 使用一个额外的参数 `flags`，如果指定书签列就需要此参数。  
  
```  
////////////////////////////////////////////////////////////////////////  
// MyProviderRS.h  
  
#define ADD_COLUMN_ENTRY(ulCols, name, ordinal, colSize, type, precision,   
scale, guid, dataClass, member) \  
   _rgColumns[ulCols].pwszName = (LPOLESTR)name; \  
   _rgColumns[ulCols].pTypeInfo = (ITypeInfo*)NULL; \  
   _rgColumns[ulCols].iOrdinal = (ULONG)ordinal; \  
   _rgColumns[ulCols].dwFlags = 0; \  
   _rgColumns[ulCols].ulColumnSize = (ULONG)colSize; \  
   _rgColumns[ulCols].wType = (DBTYPE)type; \  
   _rgColumns[ulCols].bPrecision = (BYTE)precision; \  
   _rgColumns[ulCols].bScale = (BYTE)scale; \  
   _rgColumns[ulCols].cbOffset = offsetof(dataClass, member);  
  
#define ADD_COLUMN_ENTRY_EX(ulCols, name, ordinal, colSize, type,   
precision, scale, guid, dataClass, member, flags) \  
   _rgColumns[ulCols].pwszName = (LPOLESTR)name; \  
   _rgColumns[ulCols].pTypeInfo = (ITypeInfo*)NULL; \  
   _rgColumns[ulCols].iOrdinal = (ULONG)ordinal; \  
   _rgColumns[ulCols].dwFlags = flags; \  
   _rgColumns[ulCols].ulColumnSize = (ULONG)colSize; \  
   _rgColumns[ulCols].wType = (DBTYPE)type; \  
   _rgColumns[ulCols].bPrecision = (BYTE)precision; \  
   _rgColumns[ulCols].bScale = (BYTE)scale; \  
   _rgColumns[ulCols].cbOffset = offsetof(dataClass, member); \  
   memset(&(_rgColumns[ulCols].columnid), 0, sizeof(DBID)); \  
   _rgColumns[ulCols].columnid.uName.pwszName = (LPOLESTR)name;  
```  
  
 在 `GetColumnInfo` 函数中，书签宏这样使用：  
  
```  
ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Bookmark"), 0, sizeof(DWORD),  
   DBTYPE_BYTES, 0, 0, GUID_NULL, CAgentMan, dwBookmark,   
   DBCOLUMNFLAGS_ISBOOKMARK)  
```  
  
 现在可以编译并运行增强的提供程序。  若要测试提供程序，请修改测试使用者，详见[实现简单使用者](../../data/oledb/implementing-a-simple-consumer.md)。  对提供程序运行测试使用者。  在**“测试使用者”**对话框中单击**“运行”**按钮时，验证测试使用者是否从提供程序中检索到正确的字符串。  
  
## 请参阅  
 [增强简单的只读提供程序](../../data/oledb/enhancing-the-simple-read-only-provider.md)