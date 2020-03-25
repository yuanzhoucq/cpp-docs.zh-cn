---
title: 将接口添加到提供程序
ms.date: 05/09/2019
helpviewer_keywords:
- OLE DB provider templates, object interfaces
ms.assetid: b0fc7cf8-428a-4584-9d64-ce9074d0eb66
ms.openlocfilehash: b13d1224388dc7d3218dea1c70b5aa8a595fcbdb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212326"
---
# <a name="adding-an-interface-to-your-provider"></a>将接口添加到提供程序

> [!NOTE]
> ATL OLE DB 提供程序向导不适用于 Visual Studio 2019 及更高版本。

确定要将接口添加到哪个对象中（通常是 OLE DB 提供程序向导创建的数据源、行集、命令或会话对象）。 需要将接口添加到的对象可以是提供程序暂不支持的对象。 在这种情况下，运行 ATL OLE DB 提供程序向导来创建对象。 右键单击“类视图”中的项目，依次单击菜单中的“添加” > “新项”，依次选择“已安装” > “Visual C++” > “ATL”，再单击“ATL OLEDB 提供程序”。 建议将接口代码置于独立目录中，然后将文件复制到提供程序项目。

如果已新建类来支持接口，请让对象继承自相应类。 例如，可以将类 `IRowsetIndexImpl` 添加到行集对象：

```cpp
template <class Creator>
class CCustomRowset :
    public CRowsetImpl< CCustomRowset<Creator>, CCustomWindowsFile, Creator>,
    public IRowsetIndexImpl< ... >
```

使用 COM_INTERFACE_ENTRY 宏将接口添加到对象中的 COM_MAP。 如果没有映射，请创建一个。 例如：

```cpp
BEGIN_COM_MAP(CCustomRowset)
     COM_INTERFACE_ENTRY(IRowsetIndex)
END_COM_MAP()
```

对于行集对象，链接它的父对象的映射，这样就能将对象委托给父类。 在此示例中，将 COM_INTERFACE_ENTRY_CHAIN 宏添加到映射中：

```cpp
BEGIN_COM_MAP(CCustomRowset)
     COM_INTERFACE_ENTRY(IRowsetIndex)
     COM_INTERFACE_ENTRY_CHAIN(CRowsetImpl)
END_COM_MAP()
```

## <a name="see-also"></a>另请参阅

[使用 OLE DB 提供程序模板](../../data/oledb/working-with-ole-db-provider-templates.md)
