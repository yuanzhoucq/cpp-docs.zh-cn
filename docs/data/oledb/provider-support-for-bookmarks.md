---
title: 用于书签的提供程序支持 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IRowsetLocate class, provider support for bookmarks
- OLE DB provider templates, bookmarks
- bookmarks, OLE DB
- IRowsetLocate class
- OLE DB providers, bookmark support
ms.assetid: 1b14ccff-4f76-462e-96ab-1aada815c377
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 139956fcd7d9244c486ad37797696817c7080fbd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="provider-support-for-bookmarks"></a>用于书签的提供程序支持
本主题中的示例将添加`IRowsetLocate`接口`CMyProviderRowset`类。 在几乎所有情况下，你首先将接口添加到现有的 COM 对象。 你随后可以测试它通过从使用者模板中添加更多调用。 此示例演示如何：  
  
-   将接口添加到提供程序。  
  
-   动态确定要返回给使用者的列。  
  
-   添加书签的支持。  
  
 `IRowsetLocate` 接口继承自 `IRowset` 接口。 若要添加`IRowsetLocate`接口、 继承`CMyProviderRowset`从[IRowsetLocateImpl](../../data/oledb/irowsetlocateimpl-class.md)。  
  
 添加`IRowsetLocate`接口是从大多数接口稍有不同。 若要向上 OLE DB 的 Vtable 行提供程序模板必须模板参数，以处理派生的接口。 下面的代码演示了新的继承列表：  
  
```cpp
////////////////////////////////////////////////////////////////////////  
// MyProviderRS.h  
  
// CMyProviderRowset  
class CMyProviderRowset : public CRowsetImpl< CMyProviderRowset,   
      CTextData, CMyProviderCommand, CAtlArray<CTextData>,   
      CSimpleRow,   
          IRowsetLocateImpl<CMyProviderRowset, IRowsetLocate>>  
```  
  
 第 4 个、 第五个和第六个参数都已添加。 此示例使用默认值，第四个和第五个参数但指定`IRowsetLocateImpl`作为第六个参数。 `IRowsetLocateImpl` 是一个采用两个模板参数的 OLE DB 模板类： 这些挂钩`IRowsetLocate`接口`CMyProviderRowset`类。 若要添加大多数接口，可以跳过此步骤，并将其迁移到下一步。 仅`IRowsetLocate`和`IRowsetScroll`接口需要在这种方式中处理。  
  
 然后需要告诉`CMyProviderRowset`调用`QueryInterface`为`IRowsetLocate`接口。 将行添加`COM_INTERFACE_ENTRY(IRowsetLocate)`到映射。 接口映射`CMyProviderRowset`应显示下面的代码中所示：  
  
```cpp
////////////////////////////////////////////////////////////////////////  
// MyProviderRS.h  
  
typedef CRowsetImpl< CMyProviderRowset, CTextData, CMyProviderCommand, CAtlArray<CTextData>, CSimpleRow, IRowsetLocateImpl<CMyProviderRowset, IRowsetLocate>> _RowsetBaseClass;  
  
BEGIN_COM_MAP(CMyProviderRowset)  
   COM_INTERFACE_ENTRY(IRowsetLocate)  
   COM_INTERFACE_ENTRY_CHAIN(_RowsetBaseClass)  
END_COM_MAP()  
```  
  
 你还需要将挂接到你的代码图`CRowsetImpl`类。 添加 COM_INTERFACE_ENTRY_CHAIN 宏中中将挂钩`CRowsetImpl`映射。 此外，创建名为的 typedef`RowsetBaseClass`包含的继承信息。 此 typedef 是任意参数并可以忽略。  
  
 最后，处理**IColumnsInfo::GetColumnsInfo**调用。 你通常应使用 PROVIDER_COLUMN_ENTRY 宏来执行此操作。 但是，使用者可能想要使用书签。 你必须能够更改该提供程序返回，具体取决于使用者是否要求书签的列。  
  
 若要处理**IColumnsInfo::GetColumnsInfo**调用，删除**PROVIDER_COLUMN**映射中`CTextData`类。 PROVIDER_COLUMN_MAP 宏定义了一个函数`GetColumnInfo`。 你需要定义自己`GetColumnInfo`函数。 函数声明应如下所示：  
  
```cpp
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
  
 然后，实现`GetColumnInfo`函数 MyProviderRS.cpp 文件中，如下所示：  
  
```cpp
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
  
 `GetColumnInfo` 第一个检查以确定属性是否调用**DBPROP_IRowsetLocate**设置。 OLE DB 具有每个关闭的行集对象的可选接口属性。 如果使用者想要使用这些可选接口之一，但它会将属性设置为 true。 然后，该提供程序可以检查此属性，并采取基于它的特殊操作。  
  
 在你实现中，通过使用命令对象的指针获取的属性。 `pThis`指针表示的行集或命令类。 由于你在此处使用模板，你必须将此作为传入`void`的指针或代码不编译。  
  
 指定要包含的列信息的静态数组。 如果使用者不希望书签列，数组中的一项被多余。 您可以动态地分配此数组，但你需要确保正确地销毁它。 此示例定义，并使用宏 ADD_COLUMN_ENTRY 和 ADD_COLUMN_ENTRY_EX 将信息插入到数组。 可以将宏添加到 MyProviderRS.H 文件中的以下代码所示：  
  
```cpp
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
  
 若要测试的代码在使用者，你需要进行一些更改到`OnRun`处理程序。 对函数的第一个更改是你添加代码以将属性添加到属性集。 该代码设置**DBPROP_IRowsetLocate**属性为 true，因此告知提供程序所需的书签列。 `OnRun`处理程序代码应如下显示：  
  
```cpp
//////////////////////////////////////////////////////////////////////  
// TestProv Consumer Application in TestProvDlg.cpp  
  
void CTestProvDlg::OnRun()   
{  
   CCommand<CAccessor<CProvider>> table;  
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
  
 While 循环包含用于调用代码`Compare`中的方法`IRowsetLocate`接口。 因为要比较完全相同的书签，应始终传递你拥有的代码。 此外，在临时变量中存储一个书签，以便你可以使用它段时间后循环完成调用`MoveToBookmark`的使用者模板中的函数。 `MoveToBookmark`函数调用`GetRowsAt`中的方法`IRowsetLocate`。  
  
 你还需要更新使用者中的用户记录。 在要处理书签和中的条目的类中添加一个条目**COLUMN_MAP**:  
  
```cpp
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
  
 已更新代码，你应该能够构建和执行提供程序与`IRowsetLocate`接口。  
  
## <a name="see-also"></a>请参阅  
 [高级提供程序技术](../../data/oledb/advanced-provider-techniques.md)