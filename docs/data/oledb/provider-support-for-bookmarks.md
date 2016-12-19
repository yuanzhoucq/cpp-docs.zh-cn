---
title: "用于书签的提供程序支持 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "书签, OLE DB"
  - "IRowsetLocate 类"
  - "IRowsetLocate 类, 用于书签的提供程序支持"
  - "OLE DB 提供程序模板, 书签"
  - "OLE DB 提供程序, 书签支持"
ms.assetid: 1b14ccff-4f76-462e-96ab-1aada815c377
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 用于书签的提供程序支持
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本主题中的示例将 `IRowsetLocate` 接口添加到 `CMyProviderRowset` 类。  几乎在所有情况下，都通过向现有 COM 对象添加接口开始。  然后可以通过从使用者模板添加更多的调用来测试它。  该示例演示如何：  
  
-   向提供程序添加接口。  
  
-   动态确定返回给使用者的列。  
  
-   添加书签支持。  
  
 `IRowsetLocate` 接口从 `IRowset` 接口继承。  若要添加 `IRowsetLocate` 接口，请从 [IRowsetLocateImpl](../../data/oledb/irowsetlocateimpl-class.md) 继承 `CMyProviderRowset`。  
  
 添加 `IRowsetLocate` 接口与大多数接口有点差异。  为了使 VTABLE 排成行，OLE DB 提供程序模板具有处理导出接口的模板参数。  以下代码显示新继承列表：  
  
```  
////////////////////////////////////////////////////////////////////////  
// MyProviderRS.h  
  
// CMyProviderRowset  
class CMyProviderRowset : public CRowsetImpl< CMyProviderRowset,   
      CTextData, CMyProviderCommand, CAtlArray<CTextData>,   
      CSimpleRow,   
          IRowsetLocateImpl<CMyProviderRowset, IRowsetLocate> >  
```  
  
 第四、第五和第六个参数都已添加。  此示例使用第四和第五个参数的默认值，但指定 `IRowsetLocateImpl` 为第六个参数。  `IRowsetLocateImpl` 是 OLE DB 模板类，它带有两个模板参数：这些参数将 `IRowsetLocate` 接口挂钩到 `CMyProviderRowset` 类。  对于大多数接口的添加，可以跳过这一步并移动到下一步。  只有 `IRowsetLocate` 和 `IRowsetScroll` 接口需要用这种方法处理。  
  
 然后需要通知 `CMyProviderRowset` 为 `IRowsetLocate` 接口调用 `QueryInterface`。  将行 `COM_INTERFACE_ENTRY(IRowsetLocate)` 添加到映射。  `CMyProviderRowset` 的接口映射应如下面的代码所示：  
  
```  
////////////////////////////////////////////////////////////////////////  
// MyProviderRS.h  
  
typedef CRowsetImpl< CMyProviderRowset, CTextData, CMyProviderCommand, CAtlArray<CTextData>, CSimpleRow, IRowsetLocateImpl<CMyProviderRowset, IRowsetLocate> > _RowsetBaseClass;  
  
BEGIN_COM_MAP(CMyProviderRowset)  
   COM_INTERFACE_ENTRY(IRowsetLocate)  
   COM_INTERFACE_ENTRY_CHAIN(_RowsetBaseClass)  
END_COM_MAP()  
```  
  
 还需要将映射挂钩到 `CRowsetImpl` 类中。  添加 COM\_INTERFACE\_ENTRY\_CHAIN 宏，以便挂钩到 `CRowsetImpl` 映射。  还创建一个名为 `RowsetBaseClass` 的 typedef，它由继承信息组成。  此 typedef 为任意值并可以被忽略。  
  
 最后，处理 **IColumnsInfo::GetColumnsInfo** 调用。  通常使用 PROVIDER\_COLUMN\_ENTRY 宏进行此操作。  但使用者可能想要使用书签。  必须能够根据使用者是否要求书签来更改提供程序返回的列。  
  
 若要处理 **IColumnsInfo::GetColumnsInfo** 调用，请删除 `CTextData` 类中的 **PROVIDER\_COLUMN** 映射。  PROVIDER\_COLUMN\_MAP 宏定义函数 `GetColumnInfo`。  需要定义您自己的 `GetColumnInfo` 函数。  函数声明应该是类似于这样：  
  
```  
////////////////////////////////////////////////////////////////////////  
// MyProviderRS.H  
  
class CTextData  
{  
   ...  
     // NOTE: Be sure you removed the PROVIDER_COLUMN_MAP!  
   static ATLCOLUMNINFO* GetColumnInfo(CMyProviderRowset* pThis,   
        ULONG* pcCols);  
   static ATLCOLUMNINFO* GetColumnInfo(CMyProviderCommand* pThis,   
        ULONG* pcCols);  
...  
};  
```  
  
 然后在 MyProviderRS.cpp 文件中实现 `GetColumnInfo` 函数，如下所示：  
  
```  
////////////////////////////////////////////////////////////////////  
// MyProviderRS.cpp  
  
template <class TInterface>  
ATLCOLUMNINFO* CommonGetColInfo(IUnknown* pPropsUnk, ULONG* pcCols)  
{  
   static ATLCOLUMNINFO _rgColumns[5];  
   ULONG ulCols = 0;  
  
   CComQIPtr<TInterface> spProps = pPropsUnk;  
  
   CDBPropIDSet set(DBPROPSET_ROWSET);  
   set.AddPropertyID(DBPROP_BOOKMARKS);  
   DBPROPSET* pPropSet = NULL;  
   ULONG ulPropSet = 0;  
   HRESULT hr;  
  
   if (spProps)  
      hr = spProps->GetProperties(1, &set, &ulPropSet, &pPropSet);  
  
   // Check the property flag for bookmarks, if it is set, set the   
// zero ordinal entry in the column map with the bookmark   
// information.  
  
   if (pPropSet)  
   {  
      CComVariant var = pPropSet->rgProperties[0].vValue;  
      CoTaskMemFree(pPropSet->rgProperties);  
      CoTaskMemFree(pPropSet);  
  
      if ((SUCCEEDED(hr) && (var.boolVal == VARIANT_TRUE)))  
      {  
         ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Bookmark"), 0,   
                     sizeof(DWORD), DBTYPE_BYTES,  
            0, 0, GUID_NULL, CAgentMan, dwBookmark,         
                        DBCOLUMNFLAGS_ISBOOKMARK)  
         ulCols++;  
      }  
  
   }  
  
   // Next set the other columns up.  
   ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Field1"), 1, 16, DBTYPE_STR,   
          0xFF, 0xFF, GUID_NULL, CTextData, szField1)  
   ulCols++;  
   ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Field2"), 2, 16, DBTYPE_STR,  
       0xFF, 0xFF, GUID_NULL, CTextData, szField2)  
   ulCols++;  
  
   if (pcCols != NULL)  
      *pcCols = ulCols;  
  
   return _rgColumns;  
}  
  
ATLCOLUMNINFO* CTextData::GetColumnInfo(CMyProviderCommand* pThis,   
     ULONG* pcCols)  
{  
   return CommonGetColInfo<ICommandProperties>(pThis->GetUnknown(),  
        pcCols);  
}  
  
ATLCOLUMNINFO* CAgentMan::GetColumnInfo(RUpdateRowset* pThis, ULONG* pcCols)  
{  
   return CommonGetColInfo<IRowsetInfo>(pThis->GetUnknown(), pcCols);  
}  
```  
  
 `GetColumnInfo` 首先检查是否设置了名为 **DBPROP\_IRowsetLocate** 的属性。  OLE DB 对行集合对象的每个可选接口都具有属性。  如果使用者要使用这些可选接口中的一个，它将属性设置为真。  提供程序然后可以检查该属性并根据它采取特殊的操作。  
  
 在实现中，通过使用指向命令对象的指针获取属性。  `pThis` 指针表示行集合或命令类。  因为这里使用模板，所以必须将此作为 `void` 指针传入，否则代码将不能编译。  
  
 指定静态数组以包含列信息。  如果使用者不想要书签列，则数组中的一项是多余的。  可以动态分配该数组，但需要确保适当销毁它。  本例定义并使用 ADD\_COLUMN\_ENTRY 和 ADD\_COLUMN\_ENTRY\_EX 宏将信息插入到该数组中。  可以将这些宏添加到 MyProviderRS.H 文件，如以下代码所示：  
  
```  
////////////////////////////////////////////////////////////////////////  
// MyProviderRS.h  
  
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
  
 为了在使用者中测试代码，需要对 `OnRun` 处理函数做几个更改。  对该函数的第一个更改是添加将属性添加到属性集的代码。  此代码将 **DBPROP\_IRowsetLocate** 属性设置为真，从而通知提供程序您想要书签列。  `OnRun` 处理函数代码应类似于这样：  
  
```  
//////////////////////////////////////////////////////////////////////  
// TestProv Consumer Application in TestProvDlg.cpp  
  
void CTestProvDlg::OnRun()   
{  
   CCommand<CAccessor<CProvider> > table;  
   CDataSource source;  
   CSession   session;  
  
   if (source.Open("MyProvider.MyProvider.1", NULL, NULL, NULL,   
          NULL) != S_OK)  
      return;  
  
   if (session.Open(source) != S_OK)  
      return;  
  
   CDBPropSet propset(DBPROPSET_ROWSET);  
   propset.AddProperty(DBPROP_IRowsetLocate, true);  
   if (table.Open(session, _T("c:\\public\\testprf2\\myData.txt"),   
          &propset) != S_OK)  
      return;  
  
   CBookmark<4> tempBookmark;  
   ULONG ulCount=0;  
   while (table.MoveNext() == S_OK)  
   {  
  
      DBCOMPARE compare;  
      if (ulCount == 2)  
         tempBookmark = table.bookmark;  
      HRESULT hr = table.Compare(table.dwBookmark, table.dwBookmark,  
                 &compare);  
      if (FAILED(hr))  
         ATLTRACE(_T("Compare failed: 0x%X\n"), hr);  
      else  
         _ASSERTE(compare == DBCOMPARE_EQ);  
  
      m_ctlString1.AddString(table.szField1);  
      m_ctlString2.AddString(table.szField2);  
      ulCount++;  
   }  
  
   table.MoveToBookmark(tempBookmark);  
   m_ctlString1.AddString(table.szField1);  
   m_ctlString2.AddString(table.szField2);  
}  
```  
  
 while 循环包含在 `IRowsetLocate` 接口中调用 `Compare` 方法的代码。  您拥有的代码应该总是传递，因为比较的是完全相同的书签。  另外在临时变量中存储一个书签，以便可以在 while 循环完成后用该书签调用使用者模板中的 `MoveToBookmark` 函数。  `MoveToBookmark` 函数调用 `IRowsetLocate` 中的 `GetRowsAt` 方法。  
  
 还需要更新使用者中的用户记录。  在类中添加一项以处理书签和 **COLUMN\_MAP** 中的项：  
  
```  
///////////////////////////////////////////////////////////////////////  
// TestProvDlg.cpp  
  
class CProvider  
{  
// Attributes  
public:  
   CBookmark<4>    bookmark;  // Add this line  
   char   szCommand[16];  
   char   szText[256];  
  
   // Binding Maps  
BEGIN_ACCESSOR_MAP(CProvider, 1)  
   BEGIN_ACCESSOR(0, true)   // auto accessor  
      BOOKMARK_ENTRY(bookmark)  // Add this line  
      COLUMN_ENTRY(1, szField1)  
      COLUMN_ENTRY(2, szField2)  
   END_ACCESSOR()  
END_ACCESSOR_MAP()  
};  
```  
  
 更新了代码后，应该能够用 `IRowsetLocate` 接口生成和执行提供程序。  
  
## 请参阅  
 [高级提供程序技术](../../data/oledb/advanced-provider-techniques.md)