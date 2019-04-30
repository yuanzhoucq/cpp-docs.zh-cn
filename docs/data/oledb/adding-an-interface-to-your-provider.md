---
title: 将接口添加到提供程序
ms.date: 10/29/2018
helpviewer_keywords:
- OLE DB provider templates, object interfaces
ms.assetid: b0fc7cf8-428a-4584-9d64-ce9074d0eb66
ms.openlocfilehash: c0452ca74509b65de3787af93bff41b3cb399c99
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62384967"
---
# <a name="adding-an-interface-to-your-provider"></a>将接口添加到提供程序

确定你想要添加到接口的对象 (通常由创建数据源、 行集、 命令或会话对象**OLE DB 提供程序向导**)。 可能需要将添加到接口的对象是一个您的提供程序当前不支持它。 在这种情况下，运行**ATL OLE DB 提供程序向导**来创建对象。 右键单击该项目中的**类视图**，单击**添加** > **新项**从菜单中选择**已安装** > **可视化C++**   >  **ATL**，然后单击**ATL OLEDB 提供程序**。 你可能想要将接口代码放在一个单独的目录，然后将文件复制到你提供程序的项目。

如果你创建一个新类来支持接口，请从类中继承的对象。 例如，可能会将类添加`IRowsetIndexImpl`到行集对象：

```cpp
template <class Creator>
class CCustomRowset :
    public CRowsetImpl< CCustomRowset<Creator>, CCustomWindowsFile, Creator>,
    public IRowsetIndexImpl< ... >
```

将接口添加到 COM_MAP 中，使用 COM_INTERFACE_ENTRY 宏的对象中。 如果没有映射，创建一个。 例如：

```cpp
BEGIN_COM_MAP(CCustomRowset)
     COM_INTERFACE_ENTRY(IRowsetIndex)
END_COM_MAP()
```

行集对象链的映射其父对象，以便对象可以委托给的父类。 在此示例中，将添加到地图的 COM_INTERFACE_ENTRY_CHAIN 宏：

```cpp
BEGIN_COM_MAP(CCustomRowset)
     COM_INTERFACE_ENTRY(IRowsetIndex)
     COM_INTERFACE_ENTRY_CHAIN(CRowsetImpl)
END_COM_MAP()
```

## <a name="see-also"></a>请参阅

[使用 OLE DB 提供程序模板](../../data/oledb/working-with-ole-db-provider-templates.md)