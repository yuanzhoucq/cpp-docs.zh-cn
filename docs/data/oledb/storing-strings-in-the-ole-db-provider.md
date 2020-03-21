---
title: 将字符串存储在 OLE DB 提供程序中
ms.date: 05/09/2019
helpviewer_keywords:
- user records, editing
ms.assetid: 36cb9635-067c-4cad-8f85-962f28026f6a
ms.openlocfilehash: 1d6d2b73495d5ca6e275b13ed3c430f8169179d4
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079108"
---
# <a name="storing-strings-in-the-ole-db-provider"></a>将字符串存储在 OLE DB 提供程序中

> [!NOTE]
> ATL OLE DB 提供程序向导不适用于 Visual Studio 2019 及更高版本。

在 CustomRS.h 中，ATL OLE DB 提供程序向导创建默认用户记录（称为“`CWindowsFile`”）。 若要处理两个字符串，请修改 `CWindowsFile`，如下面的代码所示：

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

数据成员 `szCommand` 和 `szText` 表示两个字符串，`szCommand2` 和 `szText2` 根据需要包含其他列。 这一简单的只读提供程序不需要数据成员 `dwBookmark`，但稍后用它来添加 `IRowsetLocate` 接口；请参阅[增强简单的只读提供程序](../../data/oledb/enhancing-the-simple-read-only-provider.md)。 `==` 运算符比较实例（可视需要实现此运算符）。

完成后，可以添加[将字符串读入 OLE DB 提供程序](../../data/oledb/reading-strings-into-the-ole-db-provider.md)这一功能。

## <a name="see-also"></a>另请参阅

[实现简单的只读提供程序](../../data/oledb/implementing-the-simple-read-only-provider.md)<br/>
