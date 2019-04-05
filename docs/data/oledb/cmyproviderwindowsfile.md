---
title: CCustomWindowsFile
ms.date: 10/22/2018
f1_keywords:
- cmyproviderwindowsfile
- ccustomwindowsfile
helpviewer_keywords:
- CMyProviderWindowsFile class
- OLE DB providers, wizard-generated files
- CCustomWindowsFile class
ms.assetid: 0e9e72ac-1e1e-445f-a7ac-690c20031f9d
ms.openlocfilehash: 4af302d8a391de359f3b8ac66d41b5d7198fd8f6
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "59033101"
---
# <a name="ccustomwindowsfile"></a>CCustomWindowsFile

向导将创建具有一个行的数据; 的类在这种情况下，名为`CCustomWindowsFile`。 下面的代码用于`CCustomWindowsFile`是向导生成和使用列出的目录中的所有文件`WIN32_FIND_DATA`结构。 `CCustomWindowsFile` 继承自`WIN32_FIND_DATA`结构：

```cpp
/////////////////////////////////////////////////////////////////////
// CustomRS.H

class CCustomWindowsFile: 
   public WIN32_FIND_DATA
{
public:
BEGIN_PROVIDER_COLUMN_MAP(CCustomWindowsFile)
   PROVIDER_COLUMN_ENTRY("FileAttributes", 1, dwFileAttributes)
   PROVIDER_COLUMN_ENTRY("FileSizeHigh", 2, nFileSizeHigh)
   PROVIDER_COLUMN_ENTRY("FileSizeLow", 3, nFileSizeLow)
   PROVIDER_COLUMN_ENTRY_STR("FileName", 4, cFileName)
   PROVIDER_COLUMN_ENTRY_STR("AltFileName", 5, cAlternateFileName)
END_PROVIDER_COLUMN_MAP()
};
```

`CCustomWindowsFile` 称为[用户记录类](../../data/oledb/user-record.md)因为它也具有描述提供程序的行集中的列的映射。 提供程序列映射包含每个字段使用 PROVIDER_COLUMN_ENTRY 宏的行集中的一个条目。 宏指定列名称，序号，和结构项的偏移量。 在上述代码中的提供程序列条目包含的偏移量`WIN32_FIND_DATA`结构。 当使用者调用`IRowset::GetData`，在一个连续的缓冲区中传输数据。 而不是让您执行指针算法，该映射，可指定数据成员。

`CCustomRowset`类还包含`Execute`方法。 `Execute` 是什么实际从本机源读取中的数据。 下面的代码显示了由向导生成`Execute`方法。 该函数使用 Win32`FindFirstFile`并`FindNextFile`Api 来检索有关目录中的文件的信息并将其放置在实例的`CCustomWindowsFile`类。

```cpp
/////////////////////////////////////////////////////////////////////
// CustomRS.H

HRESULT Execute(DBPARAMS * pParams, LONG* pcRowsAffected)
{
   USES_CONVERSION;
   BOOL bFound = FALSE;
   HANDLE hFile;
   LPTSTR  szDir = (m_strCommandText == _T("")) ? _T("*.*") :
       OLE2T(m_strCommandText);
   CCustomWindowsFile wf;
   hFile = FindFirstFile(szDir, &wf);
   if (hFile == INVALID_HANDLE_VALUE)
      return DB_E_ERRORSINCOMMAND;
   LONG cFiles = 1;
   BOOL bMoreFiles = TRUE;
   while (bMoreFiles)
   {
      if (!m_rgRowData.Add(wf))
         return E_OUTOFMEMORY;
      bMoreFiles = FindNextFile(hFile, &wf);
      cFiles++;
   }
   FindClose(hFile);
   if (pcRowsAffected != NULL)
      *pcRowsAffected = cFiles;
   return S_OK;
}
```

要搜索的目录所示`m_strCommandText`; 其中包含所表示的文本`ICommandText`中命令对象接口。 如果未不指定任何目录，则使用当前目录。

此方法创建一个条目 （对应于一行） 每个文件，并将其放入`m_rgRowData`数据成员。 `CRowsetImpl`类定义`m_rgRowData`数据成员。 此数组中的数据显示整个表，并在整个模板。

## <a name="see-also"></a>请参阅

[提供程序向导生成的文件](../../data/oledb/provider-wizard-generated-files.md)<br/>
