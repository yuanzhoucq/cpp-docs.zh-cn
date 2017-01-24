---
title: "将字符串读入 OLE DB 提供程序 | Microsoft Docs"
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
  - "OLE DB 提供程序, 读入字符串"
ms.assetid: 517f322c-f37e-4eed-bf5e-dd9a412c2f98
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 将字符串读入 OLE DB 提供程序
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`RMyProviderRowset::Execute` 函数打开文件并读取字符串。  使用者通过调用 [ICommandText::SetCommandText](https://msdn.microsoft.com/en-us/library/ms709757.aspx) 将文件名传递给提供程序。  提供程序接收文件名并将其存储在成员变量 `m_szCommandText` 中。  `Execute` 从 `m_szCommandText` 中读取文件名。  如果文件名无效或文件不可用，则 `Execute` 返回错误。  否则，它将打开文件并调用 `fgets` 检索字符串。  对于读取的每一组字符串，`Execute` 都创建用户记录 \(`CAgentMan`\) 的一个实例并将其放在数组中。  
  
 如果文件无法打开，`Execute` 必须返回 **DB\_E\_NOTABLE**。  如果它返回的是 **E\_FAIL**，提供程序将不能与许多使用者一起工作，并且不会传递 OLE DB  [测试一致性](../../data/oledb/testing-your-provider.md)。  
  
## 示例  
  
### 说明  
 编辑过的 `Execute` 函数类似于这样：  
  
### 代码  
  
```  
/////////////////////////////////////////////////////////////////////////  
// MyProviderRS.h  
class RMyProviderRowset : public CRowsetImpl< RMyProviderRowset, CAgentMan, CRMyProviderCommand>  
{  
public:  
    HRESULT Execute(DBPARAMS * pParams, LONG* pcRowsAffected)  
    {  
        enum {  
            sizeOfBuffer = 256,  
            sizeOfFile = MAX_PATH  
        };  
        USES_CONVERSION;  
        FILE* pFile = NULL;  
        TCHAR szString[sizeOfBuffer];  
        TCHAR szFile[sizeOfFile];  
        size_t nLength;        errcodeerr;  
  
        ObjectLock lock(this);  
  
        // From a filename, passed in as a command text, scan the file  
        // placing data in the data array.  
        if (!m_szCommandText)  
        {  
            ATLTRACE("No filename specified");  
            return E_FAIL;  
        }  
  
        // Open the file  
        _tcscpy_s(szFile, sizeOfFile, m_szCommandText);  
        if (szFile[0] == _T('\0') ||   
            ((err = fopen_s(&pFile, &szFile[0], "r")) == 0))  
        {  
            ATLTRACE("Could not open file");  
            return DB_E_NOTABLE;  
        }  
  
        // Scan and parse the file.  
        // The file should contain two strings per record  
        LONG cFiles = 0;  
        while (fgets(szString, sizeOfBuffer, pFile) != NULL)  
        {  
            nLength = strnlen(szString, sizeOfBuffer);  
            szString[nLength-1] = '\0';   // Strip off trailing CR/LF  
            CAgentMan am;  
            _tcscpy_s(am.szCommand, am.sizeOfCommand, szString);  
            _tcscpy_s(am.szCommand2, am.sizeOfCommand2, szString);  
  
            if (fgets(szString, sizeOfBuffer, pFile) != NULL)  
            {  
                nLength = strnlen(szString, sizeOfBuffer);  
                szString[nLength-1] = '\0'; // Strip off trailing CR/LF  
                _tcscpy_s(am.szText, am.sizeOfText, szString);  
                _tcscpy_s(am.szText2, am.sizeOfText2, szString);  
            }  
  
            am.dwBookmark = ++cFiles;  
            if (!m_rgRowData.Add(am))  
            {  
                ATLTRACE("Couldn't add data to array");  
                fclose(pFile);  
                return E_FAIL;  
            }  
        }  
  
        if (pcRowsAffected != NULL)  
            *pcRowsAffected = cFiles;  
        return S_OK;  
    }  
}  
```  
  
## 请参阅  
 [实现简单的只读提供程序](../../data/oledb/implementing-the-simple-read-only-provider.md)