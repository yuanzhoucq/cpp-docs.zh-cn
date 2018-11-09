---
title: 将字符串存储在 OLE DB 提供程序中
ms.date: 10/26/2018
helpviewer_keywords:
- user records, editing
ms.assetid: 36cb9635-067c-4cad-8f85-962f28026f6a
ms.openlocfilehash: 54dfdb347c621cf6f8645feb6d13742f32503f9f
ms.sourcegitcommit: 943c792fdabf01c98c31465f23949a829eab9aad
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2018
ms.locfileid: "51264614"
---
# <a name="storing-strings-in-the-ole-db-provider"></a>将字符串存储在 OLE DB 提供程序中

在中*自定义*RS.h， **ATL OLE DB 提供程序向导**创建默认的用户记录调用`CWindowsFile`。 若要处理两个字符串，修改`CWindowsFile`如下面的代码中所示：

```cpp
////////////////////////////////////////////////////////////////////////
class CCustomWindowsFile:
   public WIN32_FIND_DATA
{
public:
DWORD dwBookmark;
static const int iSize = 256;    // Add this
TCHAR szCommand[iSize];          // Add this
TCHAR szText[iSize];             // Add this
TCHAR szCommand2[iSize];         // Add this
TCHAR szText2[iSize];            // Add this

BEGIN_PROVIDER_COLUMN_MAP(CCustomWindowsFile)
   PROVIDER_COLUMN_ENTRY("FileAttributes", 1, dwFileAttributes)
   PROVIDER_COLUMN_ENTRY("FileSizeHigh", 2, nFileSizeHigh)
   PROVIDER_COLUMN_ENTRY("FileSizeLow", 3, nFileSizeLow)
   PROVIDER_COLUMN_ENTRY_STR("FileName", 4, cFileName)
   PROVIDER_COLUMN_ENTRY_STR("AltFileName", 5, cAlternateFileName)

   PROVIDER_COLUMN_ENTRY_STR("Command", 6, szCommand)    // Add this
   PROVIDER_COLUMN_ENTRY_STR("Text", 7, szText)          // Add this
   PROVIDER_COLUMN_ENTRY_STR("Command2", 8, szCommand2)  // Add this
   PROVIDER_COLUMN_ENTRY_STR("Text2", 9, szText2)        // Add this
END_PROVIDER_COLUMN_MAP()

   bool operator==(const CCustomWindowsFile& am) // This is optional
   {
      return (lstrcmpi(cFileName, am.cFileName) == 0);
   }
};
```

数据成员`szCommand`并`szText`表示两个字符串，并将`szCommand2`和`szText2`具有必要的其他列。 数据成员`dwBookmark`的此简单的只读提供程序不需要但更高版本用于添加`IRowsetLocate`接口; 请参阅[增强简单读取仅提供程序](../../data/oledb/enhancing-the-simple-read-only-provider.md)。 `==`实例进行比较的运算符 （实现此运算符是可选的）。

完成此操作后，您可以添加的功能[将字符串读入 OLE DB 访问接口](../../data/oledb/reading-strings-into-the-ole-db-provider.md)。

## <a name="see-also"></a>请参阅

[实现简单的只读提供程序](../../data/oledb/implementing-the-simple-read-only-provider.md)<br/>
