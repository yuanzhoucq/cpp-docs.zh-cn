---
title: 字符串读入 OLE DB 提供程序 |Microsoft Docs
ms.custom: ''
ms.date: 10/13/2018
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, reading strings into
ms.assetid: 517f322c-f37e-4eed-bf5e-dd9a412c2f98
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 6521ed8078f4411b704678b53f16fbdbc4d04e73
ms.sourcegitcommit: c045c3a7e9f2c7e3e0de5b7f9513e41d8b6d19b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2018
ms.locfileid: "49989874"
---
# <a name="reading-strings-into-the-ole-db-provider"></a>将字符串读入 OLE DB 提供程序

`RCustomRowset::Execute`函数打开的文件和读取字符串。 使用者将文件名传递给提供程序，通过调用[icommandtext:: Setcommandtext](/previous-versions/windows/desktop/ms709757)。 提供程序接收的文件的名称，并将其存储在成员变量`m_szCommandText`。 `Execute` 读取的文件名的`m_szCommandText`。 如果文件名无效或文件不可用，`Execute`返回错误。 否则，它会打开该文件并调用`fgets`检索字符串。 为每个集的字符串它读取`Execute`创建的用户记录实例 (`CAgentMan`) 并将其放到一个数组。  
  
如果无法打开该文件，`Execute`必须返回 DB_E_NOTABLE。 如果改为返回 E_FAIL，提供程序不会使用多个使用者和未通过 OLE DB[一致性测试](../../data/oledb/testing-your-provider.md)。  
  
## <a name="example"></a>示例  

已编辑`Execute`函数如下所示：  
  
```cpp
/////////////////////////////////////////////////////////////////////////  
// CustomRS.h  
class RCustomRowset : public CRowsetImpl< RCustomRowset, CAgentMan, CRCustomCommand>  
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
  
## <a name="see-also"></a>请参阅  

[实现简单的只读提供程序](../../data/oledb/implementing-the-simple-read-only-provider.md)