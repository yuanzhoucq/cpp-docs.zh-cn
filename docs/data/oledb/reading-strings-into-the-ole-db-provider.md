---
title: 将字符串读入 OLE DB 提供程序
ms.date: 10/13/2018
helpviewer_keywords:
- OLE DB providers, reading strings into
ms.assetid: 517f322c-f37e-4eed-bf5e-dd9a412c2f98
ms.openlocfilehash: d46b4e1a53e7e489763f40e7a5238e65b493f7c8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62283786"
---
# <a name="reading-strings-into-the-ole-db-provider"></a>将字符串读入 OLE DB 提供程序

`CCustomRowset::Execute`函数打开的文件和读取字符串。 使用者将文件名传递给提供程序，通过调用[icommandtext:: Setcommandtext](/previous-versions/windows/desktop/ms709757(v=vs.85))。 提供程序接收的文件的名称，并将其存储在成员变量`m_strCommandText`。 `Execute` 读取的文件名的`m_strCommandText`。 如果文件名无效或文件不可用，`Execute`返回错误。 否则，它会打开该文件并调用`fgets`检索字符串。 为每个集的字符串它读取`Execute`创建的用户记录实例 (修改`CCustomWindowsFile`从[OLE DB 提供程序中存储字符串](../../data/oledb/storing-strings-in-the-ole-db-provider.md)) 并将其放到一个数组。

如果无法打开该文件，`Execute`必须返回 DB_E_NOTABLE。 如果改为返回 E_FAIL，提供程序不会使用多个使用者并不会传递 OLE DB[一致性测试](../../data/oledb/testing-your-provider.md)。

## <a name="example"></a>示例

```cpp
/////////////////////////////////////////////////////////////////////////
// CustomRS.h
class CCustomRowset : public CRowsetImpl< CCustomRowset, CCustomWindowsFile, CCustomCommand>
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
        size_t nLength;

        ObjectLock lock(this);

        // From a filename, passed in as a command text, scan the file
        // placing data in the data array.
        if (!m_strCommandText)
        {
            ATLTRACE("No filename specified");
            return E_FAIL;
        }

        // Open the file
        _tcscpy_s(szFile, sizeOfFile, m_strCommandText);
        if (szFile[0] == _T('\0') ||
            (fopen_s(&pFile, (char*)&szFile[0], "r") == 0))
        {
            ATLTRACE("Could not open file");
            return DB_E_NOTABLE;
        }

        // Scan and parse the file.
        // The file should contain two strings per record
        LONG cFiles = 0;
        while (fgets((char*)szString, sizeOfBuffer, pFile) != NULL)
        {
            nLength = strnlen((char*)szString, sizeOfBuffer);
            szString[nLength-1] = '\0';   // Strip off trailing CR/LF
            CCustomWindowsFile am;
            _tcscpy_s(am.szCommand, am.iSize, szString);
            _tcscpy_s(am.szCommand2, am.iSize, szString);

            if (fgets((char*)szString, sizeOfBuffer, pFile) != NULL)
            {
                nLength = strnlen((char*)szString, sizeOfBuffer);
                szString[nLength-1] = '\0'; // Strip off trailing CR/LF
                _tcscpy_s(am.szText, am.iSize, szString);
                _tcscpy_s(am.szText2, am.iSize, szString);
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
};
```

完成此操作后，您的提供程序应可以随时编译和运行。 若要测试的提供程序，需要具有匹配功能的使用者。 [实现简单使用者](../../data/oledb/implementing-a-simple-consumer.md)演示如何创建此类测试使用者。 使用提供程序运行测试使用者，并验证测试使用者从提供程序检索到正确的字符串。

当你已成功在测试您的提供程序时，你可能想要通过实现附加接口增强其功能。 一个示例所示[增强简单的只读提供程序](../../data/oledb/enhancing-the-simple-read-only-provider.md)。

## <a name="see-also"></a>请参阅

[实现简单的只读提供程序](../../data/oledb/implementing-the-simple-read-only-provider.md)<br/>
