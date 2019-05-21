---
title: 用户记录
ms.date: 05/09/2019
helpviewer_keywords:
- records, user
- OLE DB providers, user record
- user records
- user records, described
- rowsets, user record
ms.assetid: 9c0d2864-2738-4f62-a750-1016d9c3523f
ms.openlocfilehash: d6920a73f107f226cc31cb27fd15178f6d2f1c26
ms.sourcegitcommit: 00e26915924869cd7eb3c971a7d0604388abd316
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/10/2019
ms.locfileid: "65525254"
---
# <a name="user-record"></a>用户记录

> [!NOTE] 
> ATL OLE DB 提供程序向导不适用于 Visual Studio 2019 及更高版本。

用户记录提供表示行集的列数据的代码和数据结构。 可以在编译时或运行时创建用户记录。 当你使用 ATL OLE DB 提供程序向导创建提供程序时，向导会创建如下所示的默认用户记录（假设指定了提供程序名称 [短名称] MyProvider）：

```cpp
class CWindowsFile:
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

OLE DB 提供程序模板处理与客户端交互方面的所有 OLE DB 详细信息。 为了获取响应所需的列数据，提供程序调用 `GetColumnInfo` 函数（必须将此函数置于用户记录中）。 可以显式重写用户记录中的 `GetColumnInfo`，例如通过在 .h 文件中声明它，如下所示：

```cpp
template <class T>
static ATLCOLUMNINFO* GetColumnInfo(T* pThis, ULONG* pcCols) 
```

这相当于：

```cpp
static ATLCOLUMNINFO* GetColumnInfo(CommandClass* pThis, ULONG* pcCols)
static ATLCOLUMNINFO* GetColumnInfo(RowsetClass* pThis, ULONG* pcCols)
```

然后，在用户记录的 .cpp 文件中实现 `GetColumnInfo`。

PROVIDER_COLUMN_MAP 宏有助于创建 `GetColumnInfo` 函数：

- BEGIN_PROVIDER_COLUMN_MAP 定义函数原型和 `ATLCOLUMNINFO` 结构的静态数组。

- PROVIDER_COLUMN_ENTRY 定义并初始化一个 `ATLCOLUMNINFO`。

- END_PROVIDER_COLUMN_MAP 关闭数组和函数。 它还将数组元素计数置于 pcCols 参数中。

当用户记录在运行时创建后，`GetColumnInfo` 使用 pThis 参数来接收指向行集或命令实例的指针。 命令和行集必须支持 `IColumnsInfo` 接口，这样才能从此指针获取列信息。

`CommandClass` 和 `RowsetClass` 是使用用户记录的命令和行集。

有关如何重写用户记录中 `GetColumnInfo` 的更详细示例，请参阅[动态确定返回给使用者的列](../../data/oledb/dynamically-determining-columns-returned-to-the-consumer.md)。

## <a name="see-also"></a>请参阅

[OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
