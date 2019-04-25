---
title: 动态确定返回给使用者的列
ms.date: 10/26/2018
helpviewer_keywords:
- bookmarks [C++], dynamically determining columns
- dynamically determining columns [C++]
ms.assetid: 58522b7a-894e-4b7d-a605-f80e900a7f5f
ms.openlocfilehash: 81353581d22f3d075fd19d783591ec856c21e241
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62175493"
---
# <a name="dynamically-determining-columns-returned-to-the-consumer"></a>动态确定返回给使用者的列

PROVIDER_COLUMN_ENTRY 宏通常处理`IColumnsInfo::GetColumnsInfo`调用。 但是，使用者可能选择使用书签，因为提供程序必须能够更改具体取决于是否使用者要求书签返回的列。

若要处理`IColumnsInfo::GetColumnsInfo`调用中，删除 PROVIDER_COLUMN_MAP，定义了一个函数`GetColumnInfo`，从`CCustomWindowsFile`中的用户记录*自定义*RS.h 并将其替换为你自己的定义为`GetColumnInfo`函数：

```cpp
////////////////////////////////////////////////////////////////////////
// CustomRS.H
class CCustomWindowsFile
{
public:
   DWORD dwBookmark;
   static const int iSize = 256;
   TCHAR szCommand[iSize];
   TCHAR szText[iSize];
   TCHAR szCommand2[iSize];
   TCHAR szText2[iSize];
  
   static ATLCOLUMNINFO* GetColumnInfo(void* pThis, ULONG* pcCols);
   bool operator==(const CCustomWindowsFile& am)
   {
      return (lstrcmpi(szCommand, am.szCommand) == 0);
   }
};
```

接下来，实现`GetColumnInfo`函数，在*自定义*RS.cpp，如下面的代码中所示。

`GetColumnInfo` 首先检查是否 OLE DB 属性`DBPROP_BOOKMARKS`设置。 要获取其属性`GetColumnInfo`使用指针 (`pRowset`) 到行集对象。 `pThis`指针表示创建了行集，这是存储的属性映射的类的类。 `GetColumnInfo` 类型强制转换`pThis`指针，指向`RCustomRowset`指针。

若要检查`DBPROP_BOOKMARKS`属性，`GetColumnInfo`使用`IRowsetInfo`接口，可以通过调用获取`QueryInterface`上`pRowset`接口。 作为替代方法，你可以使用 ATL [CComQIPtr](../../atl/reference/ccomqiptr-class.md)方法相反。

```cpp
////////////////////////////////////////////////////////////////////
// CustomRS.cpp
ATLCOLUMNINFO* CCustomWindowsFile::GetColumnInfo(void* pThis, ULONG* pcCols)
{
   static ATLCOLUMNINFO _rgColumns[5];
   ULONG ulCols = 0;
  
   // Check the property flag for bookmarks; if it is set, set the zero 
   // ordinal entry in the column map with the bookmark information.
   CCustomRowset* pRowset = (CCustomRowset*) pThis;
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
         DBTYPE_BYTES, 0, 0, GUID_NULL, CCustomWindowsFile, dwBookmark, 
         DBCOLUMNFLAGS_ISBOOKMARK)
         ulCols++;
      }
   }
  
   // Next, set the other columns up.
   ADD_COLUMN_ENTRY(ulCols, OLESTR("Command"), 1, 256, DBTYPE_STR, 0xFF, 0xFF, 
      GUID_NULL, CCustomWindowsFile, szCommand)
   ulCols++;
   ADD_COLUMN_ENTRY(ulCols, OLESTR("Text"), 2, 256, DBTYPE_STR, 0xFF, 0xFF, 
      GUID_NULL, CCustomWindowsFile, szText)
   ulCols++;
  
   ADD_COLUMN_ENTRY(ulCols, OLESTR("Command2"), 3, 256, DBTYPE_STR, 0xFF, 0xFF, 
      GUID_NULL, CCustomWindowsFile, szCommand2)
   ulCols++;
   ADD_COLUMN_ENTRY(ulCols, OLESTR("Text2"), 4, 256, DBTYPE_STR, 0xFF, 0xFF, 
      GUID_NULL, CCustomWindowsFile, szText2)
   ulCols++;
  
   if (pcCols != NULL)
      *pcCols = ulCols;
  
   return _rgColumns;
}
```

此示例使用静态数组来保存列信息。 如果使用者不想要书签列，则不使用数组中的一个条目。 若要处理的信息，您可以创建两个数组宏：ADD_COLUMN_ENTRY 和 ADD_COLUMN_ENTRY_EX。 ADD_COLUMN_ENTRY_EX 采用了额外的参数，*标志*，也就是说，当你指定的书签列时才需要。

```cpp
////////////////////////////////////////////////////////////////////////  
// CustomRS.h  
  
#define ADD_COLUMN_ENTRY(ulCols, name, ordinal, colSize, type, precision, scale, guid, dataClass, member) \  
   _rgColumns[ulCols].pwszName = (LPOLESTR)name; \  
   _rgColumns[ulCols].pTypeInfo = (ITypeInfo*)NULL; \  
   _rgColumns[ulCols].iOrdinal = (ULONG)ordinal; \  
   _rgColumns[ulCols].dwFlags = 0; \  
   _rgColumns[ulCols].ulColumnSize = (ULONG)colSize; \  
   _rgColumns[ulCols].wType = (DBTYPE)type; \  
   _rgColumns[ulCols].bPrecision = (BYTE)precision; \  
   _rgColumns[ulCols].bScale = (BYTE)scale; \  
   _rgColumns[ulCols].cbOffset = offsetof(dataClass, member);  
  
#define ADD_COLUMN_ENTRY_EX(ulCols, name, ordinal, colSize, type, precision, scale, guid, dataClass, member, flags) \  
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

在`GetColumnInfo`函数，书签宏用法如下：

```cpp
ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Bookmark"), 0, sizeof(DWORD),
   DBTYPE_BYTES, 0, 0, GUID_NULL, CAgentMan, dwBookmark,
   DBCOLUMNFLAGS_ISBOOKMARK)
```

你现在可以编译并运行增强的提供程序。 若要测试的提供程序，修改测试使用者中所述[实现简单使用者](../../data/oledb/implementing-a-simple-consumer.md)。 使用提供程序运行测试使用者，并验证测试使用者从提供程序检索到正确的字符串。

## <a name="see-also"></a>请参阅

[增强简单的只读提供程序](../../data/oledb/enhancing-the-simple-read-only-provider.md)<br/>
