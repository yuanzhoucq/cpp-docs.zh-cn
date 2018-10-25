---
title: CCustomWindowsFile |Microsoft Docs
ms.custom: ''
ms.date: 10/22/2018
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- cmyproviderwindowsfile
- ccustomwindowsfile
dev_langs:
- C++
helpviewer_keywords:
- CMyProviderWindowsFile class
- OLE DB providers, wizard-generated files
- CCustomWindowsFile class
ms.assetid: 0e9e72ac-1e1e-445f-a7ac-690c20031f9d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 947efa181a6b632050c01c4f2b327cf11a113e3f
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50070928"
---
# <a name="ccustomwindowsfile"></a>CCustomWindowsFile

该向导创建一个类以包含一个行的数据;在这种情况下，名为`CCustomWindowsFile`。 下面的代码用于`CCustomWindowsFile`是向导生成和使用列出的目录中的所有文件`WIN32_FIND_DATA`结构。 `CCustomWindowsFile` 继承自`WIN32_FIND_DATA`结构：

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

`CCustomWindowsFile` 称为[用户记录类](../../data/oledb/user-record.md)因为它还包含描述提供程序的行集中的列映射。 提供程序列映射包含每个字段使用 PROVIDER_COLUMN_ENTRY 宏的行集中的一个条目。 宏指定列名称，序号，和结构项的偏移量。 在上述代码中的提供程序列条目包含的偏移量`WIN32_FIND_DATA`结构。 当使用者调用`IRowset::GetData`，在一个连续的缓冲区中传输数据。 而不是让您执行指针算法，该映射，可指定数据成员。

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

表示要搜索的目录`m_strCommandText`; 其中包含所表示的文本`ICommandText`中命令对象接口。 如果未不指定任何目录，则使用当前目录。

此方法创建一个条目 （对应于一行） 每个文件，并将其放入`m_rgRowData`数据成员。 `CRowsetImpl`类定义`m_rgRowData`数据成员。 此数组中的数据表示整个表，并在整个模板。

## <a name="see-also"></a>请参阅

[提供程序向导生成的文件](../../data/oledb/provider-wizard-generated-files.md)