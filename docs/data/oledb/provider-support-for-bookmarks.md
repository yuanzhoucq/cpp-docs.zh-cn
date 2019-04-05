---
title: 用于书签的提供程序支持
ms.date: 11/04/2016
helpviewer_keywords:
- IRowsetLocate class, provider support for bookmarks
- OLE DB provider templates, bookmarks
- bookmarks, OLE DB
- IRowsetLocate class
- OLE DB providers, bookmark support
ms.assetid: 1b14ccff-4f76-462e-96ab-1aada815c377
ms.openlocfilehash: 207dcc92cd308052e4e5e7265bf0632c5096bed4
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "59041067"
---
# <a name="provider-support-for-bookmarks"></a>用于书签的提供程序支持

本主题中的示例将添加`IRowsetLocate`接口`CCustomRowset`类。 在几乎所有情况下，您首先将接口添加到现有的 COM 对象。 然后可以通过从使用者模板添加更多调用来测试它。 示例演示了如何：

- 将接口添加到提供程序。

- 动态确定要返回给使用者的列。

- 添加书签支持。

`IRowsetLocate` 接口继承自 `IRowset` 接口。 若要添加`IRowsetLocate`接口中，继承`CCustomRowset`从[IRowsetLocateImpl](../../data/oledb/irowsetlocateimpl-class.md)。

添加`IRowsetLocate`接口是从大多数界面稍有不同。 若要使 Vtable 对齐，OLE DB 提供程序模板具有模板参数，以处理派生的接口。 下面的代码显示了新的继承列表：

```cpp
////////////////////////////////////////////////////////////////////////
// CustomRS.h

// CCustomRowset
class CCustomRowset : public CRowsetImpl< CCustomRowset,
      CTextData, CCustomCommand, CAtlArray<CTextData>,
      CSimpleRow,
          IRowsetLocateImpl<CCustomRowset, IRowsetLocate>>
```

第四个、 第五个和第六个参数都已添加。 此示例使用默认值为第四和第五个参数但指定`IRowsetLocateImpl`作为第六个参数。 `IRowsetLocateImpl` 是一个 OLE DB 模板类，采用两个模板参数： 这些挂钩`IRowsetLocate`接口`CCustomRowset`类。 若要添加大多数接口，可以跳过此步骤并移动到下一个。 仅`IRowsetLocate`和`IRowsetScroll`接口需要以这种方式进行处理。

然后，你需要告诉`CCustomRowset`来调用`QueryInterface`为`IRowsetLocate`接口。 将行添加`COM_INTERFACE_ENTRY(IRowsetLocate)`到映射。 接口映射`CCustomRowset`应显示下面的代码所示：

```cpp
////////////////////////////////////////////////////////////////////////
// CustomRS.h

typedef CRowsetImpl< CCustomRowset, CTextData, CCustomCommand, CAtlArray<CTextData>, CSimpleRow, IRowsetLocateImpl<CCustomRowset, IRowsetLocate>> _RowsetBaseClass;

BEGIN_COM_MAP(CCustomRowset)
   COM_INTERFACE_ENTRY(IRowsetLocate)
   COM_INTERFACE_ENTRY_CHAIN(_RowsetBaseClass)
END_COM_MAP()
```

此外需要将挂钩到您的映射`CRowsetImpl`类。 添加在 COM_INTERFACE_ENTRY_CHAIN 宏挂接`CRowsetImpl`映射。 此外，创建名为的 typedef `RowsetBaseClass` ，它包含继承信息。 Typedef 是任意参数并被忽略。

最后，处理`IColumnsInfo::GetColumnsInfo`调用。 PROVIDER_COLUMN_ENTRY 宏通常将用于执行此操作。 但是，使用者可能想要使用的书签。 您必须能够更改具体取决于是否使用者要求书签的提供程序返回的列。

若要处理`IColumnsInfo::GetColumnsInfo`调用，请删除中的 PROVIDER_COLUMN 映射`CTextData`类。 PROVIDER_COLUMN_MAP 宏可定义一个函数`GetColumnInfo`。 定义你自己`GetColumnInfo`函数。 函数声明应如下所示：

```cpp
////////////////////////////////////////////////////////////////////////
// CustomRS.H

class CTextData
{
   ...
     // NOTE: Be sure you removed the PROVIDER_COLUMN_MAP!
   static ATLCOLUMNINFO* GetColumnInfo(CCustomRowset* pThis,
        ULONG* pcCols);
   static ATLCOLUMNINFO* GetColumnInfo(CCustomCommand* pThis,
        ULONG* pcCols);
...
};
```

然后，实现`GetColumnInfo`函数，在*自定义*RS.cpp 文件，如下所示：

```cpp
////////////////////////////////////////////////////////////////////
// CustomRS.cpp

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

ATLCOLUMNINFO* CTextData::GetColumnInfo(CCustomCommand* pThis,
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

`GetColumnInfo` 首先会查看是否某个属性调用`DBPROP_IRowsetLocate`设置。 OLE DB 已关闭的行集对象的可选接口的每个属性。 如果使用者想要使用这些可选接口之一，但它会将属性设置为 true。 提供程序随后可以检查此属性，并执行基于它的特殊操作。

在实现中，通过使用命令对象的指针获取的属性。 `pThis`指针表示的行集或命令的类。 因为你在此处使用模板，你必须将此作为传入**void**的指针或代码无法编译。

指定静态数组来保存列信息。 如果使用者不想要书签列，数组中的一项被多余。 您可以动态地分配此数组，但需要确保正确地销毁该。 此示例定义，并使用宏 ADD_COLUMN_ENTRY 和 ADD_COLUMN_ENTRY_EX 将信息插入到数组。 您可以添加到宏*自定义*RS。H 文件中的以下代码所示：

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

若要测试此代码中使用者，需要进行一些更改到`OnRun`处理程序。 对函数的第一个更改是添加代码以将属性添加到属性集。 代码集`DBPROP_IRowsetLocate`属性设为 true，从而告知提供程序所需的书签列。 `OnRun`处理程序代码应如下显示：

```cpp
//////////////////////////////////////////////////////////////////////
// TestProv Consumer Application in TestProvDlg.cpp

void CTestProvDlg::OnRun()
{
   CCommand<CAccessor<CProvider>> table;
   CDataSource source;
   CSession   session;

   if (source.Open("Custom.Custom.1", NULL, NULL, NULL,
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

**虽然**循环包含调用代码`Compare`中的方法`IRowsetLocate`接口。 您拥有的代码应始终传递，因为比较完全相同的书签。 此外，在临时变量中存储一个书签，以便您可以使用它后**虽然**循环完成调用`MoveToBookmark`使用者模板中的函数。 `MoveToBookmark`函数调用`GetRowsAt`中的方法`IRowsetLocate`。

此外需要更新使用者中的用户记录。 要处理一个书签和 COLUMN_MAP 中的条目的类中添加一个条目：

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

当更新了代码后时，您应该能够生成并执行与提供程序`IRowsetLocate`接口。

## <a name="see-also"></a>请参阅

[高级提供程序技术](../../data/oledb/advanced-provider-techniques.md)