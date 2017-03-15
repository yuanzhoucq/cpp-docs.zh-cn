---
title: "CMyProviderWindowsFile | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cmyproviderwindowsfile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMyProviderWindowsFile 类"
  - "OLE DB 提供程序, 向导生成的文件"
ms.assetid: 0e9e72ac-1e1e-445f-a7ac-690c20031f9d
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# CMyProviderWindowsFile
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

向导创建包含一行数据的类；此例中它称为 `CMyProviderWindowsFile`。  以下 `CMyProviderWindowsFile` 的代码是向导生成的，它使用 **WIN32\_FIND\_DATA** 结构列出目录中的所有文件。  `CMyProviderWindowsFile` 从 **WIN32\_FIND\_DATA** 结构继承：  
  
```  
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
  
 `CMyProviderWindowsFile` 称为[用户记录类](../../data/oledb/user-record.md)，因为它也包含描述提供程序行集合中的列的映射。  提供程序列映射使用 PROVIDER\_COLUMN\_ENTRY 宏为行集合中的每个字段都包含一项。  该宏指定结构项的列名、序号和偏移量。  以上代码中的提供程序列项包含 **WIN32\_FIND\_DATA** 结构中的偏移量。  当使用者调用 **IRowset::GetData** 时，数据在一个连续缓冲区中传输。  映射不是使您进行指针算法，而是允许您指定数据成员。  
  
 `CMyProviderRowset` 类也包含 `Execute` 方法。  `Execute` 是实际从本机源中读取数据的方法。  以下代码显示向导生成的 `Execute` 方法。  函数使用 Win32 **FindFirstFile** 和 `FindNextFile` API 检索目录中的文件信息并将它们放在 `CMyProviderWindowsFile` 类的实例中。  
  
```  
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
  
 要搜索的目录由 `m_strCommandText` 表示；它包含命令对象中由 `ICommandText` 接口表示的文本。  如果未指定目录，它使用当前目录。  
  
 该方法为每个文件创建一项（与行对应）并将其放在 **m\_rgRowData** 数据成员中。  `CRowsetImpl` 类定义 **m\_rgRowData** 数据成员。  该数组中的数据表示整个表并在整个模板中使用。  
  
## 请参阅  
 [提供程序向导生成的文件](../../data/oledb/provider-wizard-generated-files.md)