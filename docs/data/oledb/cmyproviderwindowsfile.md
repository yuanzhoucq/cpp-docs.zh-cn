---
title: CMyProviderWindowsFile | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cmyproviderwindowsfile
dev_langs:
- C++
helpviewer_keywords:
- CMyProviderWindowsFile class
- OLE DB providers, wizard-generated files
ms.assetid: 0e9e72ac-1e1e-445f-a7ac-690c20031f9d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5f9549dc81529f4c045a0f27a169516070a09900
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="cmyproviderwindowsfile"></a>CMyProviderWindowsFile
该向导创建一个类以包含一行数据;在这种情况下，调用`CMyProviderWindowsFile`。 下面的代码的`CMyProviderWindowsFile`是生成的向导并通过使用列出目录中的所有文件**WIN32_FIND_DATA**结构。 `CMyProviderWindowsFile` 继承自**WIN32_FIND_DATA**结构：  
  
```cpp
/////////////////////////////////////////////////////////////////////  
// MyProviderRS.H  
  
class CMyProviderWindowsFile:   
   public WIN32_FIND_DATA  
{  
public:  
BEGIN_PROVIDER_COLUMN_MAP(CMyProviderWindowsFile)  
   PROVIDER_COLUMN_ENTRY("FileAttributes", 1, dwFileAttributes)  
   PROVIDER_COLUMN_ENTRY("FileSizeHigh", 2, nFileSizeHigh)  
   PROVIDER_COLUMN_ENTRY("FileSizeLow", 3, nFileSizeLow)  
   PROVIDER_COLUMN_ENTRY_STR("FileName", 4, cFileName)  
   PROVIDER_COLUMN_ENTRY_STR("AltFileName", 5, cAlternateFileName)  
END_PROVIDER_COLUMN_MAP()  
};  
```  
  
 `CMyProviderWindowsFile` 调用[用户记录类](../../data/oledb/user-record.md)因为它还包含描述提供程序的行集中的列的映射。 提供程序列映射包含每个字段中使用 PROVIDER_COLUMN_ENTRY 宏的行集的一项。 该宏指定列名称，序号、 和到结构条目偏移量。 在上述代码中的提供程序列条目包含偏移量到**WIN32_FIND_DATA**结构。 当使用者调用**irowset:: Getdata**，在一个连续的缓冲区中传输数据。 而不是让你执行指针算法，该映射，可指定数据成员。  
  
 `CMyProviderRowset`类还包含`Execute`方法。 `Execute` 是什么实际本机从源读取中的数据。 下面的代码演示向导生成`Execute`方法。 该函数使用 Win32 **FindFirstFile**和`FindNextFile`Api 检索有关目录中的文件的信息并将其放在的实例中`CMyProviderWindowsFile`类。  
  
```cpp
/////////////////////////////////////////////////////////////////////  
// MyProviderRS.H  
  
HRESULT Execute(DBPARAMS * pParams, LONG* pcRowsAffected)  
{  
   USES_CONVERSION;  
   BOOL bFound = FALSE;  
   HANDLE hFile;  
   LPTSTR  szDir = (m_strCommandText == _T("")) ? _T("*.*") :  
       OLE2T(m_strCommandText);  
   CMyProviderWindowsFile wf;  
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
  
 要搜索的目录都由`m_strCommandText`; 这包含所表示的文本`ICommandText`命令对象中的接口。 如果没有指定目录，它使用当前目录。  
  
 该方法将创建的每个文件 （对应于行） 的一个项，并将其放入**m_rgRowData**数据成员。 `CRowsetImpl`类定义**m_rgRowData**数据成员。 此数组中的数据表示整个表，并在整个模板。  
  
## <a name="see-also"></a>请参阅  
 [提供程序向导生成的文件](../../data/oledb/provider-wizard-generated-files.md)