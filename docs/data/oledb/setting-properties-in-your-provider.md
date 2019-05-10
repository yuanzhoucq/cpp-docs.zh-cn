---
title: 在提供程序中设置属性
ms.date: 10/29/2018
helpviewer_keywords:
- OLE DB providers, properties
- properties [C++], OLE DB provider
ms.assetid: 26a8b493-7ec4-4686-96d0-9ad5d2bca5ac
ms.openlocfilehash: 2cbb334ab15912fdcf6980461016976d869f5a84
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62404502"
---
# <a name="setting-properties-in-your-provider"></a>在提供程序中设置属性

找到所需的属性的属性组和属性 ID。 有关详细信息，请参阅[OLE DB 属性](/previous-versions/windows/desktop/ms722734(v=vs.85))中**OLE DB 程序员参考**。

在向导生成的提供程序代码中，找到的属性组相对应的属性映射。 属性组的名称通常对应于对象的名称。 在命令或行集; 中找不到命令和行集属性可以在数据源对象中找到数据源和初始化属性。

属性映射中添加[PROPERTY_INFO_ENTRY_EX](../../data/oledb/property-info-entry-ex.md)宏。 PROPERTY_INFO_ENTRY_EX 采用四个参数：

- 对您的属性相对应的属性 ID。 从属性名称的前面删除的前七个字符 ("DBPROP_")。 例如，如果你想要添加`DBPROP_MAXROWS`，将传递`MAXROWS`的第一个元素。 如果这是自定义属性，则传递 GUID 的全名 (例如， `DBMYPROP_MYPROPERTY`)。

- 属性的变体类型 (在[OLE DB 属性](/previous-versions/windows/desktop/ms722734(v=vs.85))中**OLE DB 程序员参考**)。 输入 | VT_ 类型 （如 VT_BOOL 或 VT_I2） 相对应的数据类型。

- 标志以指示属性是否可读和可写以及它所属的组。 例如，下面的代码指示属于组的行集的读/写属性：

    ```cpp
    DBPROPFLAGS_ROWSET | DBPROPFLAGS_READ | DBPROPFLAGS_WRITE
    ```

- 属性的基值。 这可能是`VARIANT_FALSE`键入一个布尔值或零的整数类型，例如。 该属性具有此值，除非被更改。

    > [!NOTE]
    > 某些属性是连接或链接到其他属性，如书签或更新。 当使用者将一个属性设置为 true 时，也可以设置另一个属性。 OLE DB 提供程序模板支持此功能通过方法[cutlprops:: Onpropertychanged](../../data/oledb/cutlprops-onpropertychanged.md)。

## <a name="properties-ignored-by-microsoft-ole-db-providers"></a>Microsoft OLE DB 访问接口忽略的属性

Microsoft OLE DB 访问接口忽略以下 OLE DB 属性：

- `DBPROP_MAXROWS` 仅适用于只读提供程序 (即，`DBPROP_IRowsetChange`并`DBPROP_IRowsetUpdate`都**false**); 否则此属性不受支持。

- `DBPROP_MAXPENDINGROWS` 将被忽略;提供程序指定其自己的限制。

- `DBPROP_MAXOPENROWS` 将被忽略;提供程序指定其自己的限制。

- `DBPROP_CANHOLDROWS` 将被忽略;提供程序指定其自己的限制。

## <a name="see-also"></a>请参阅

[使用 OLE DB 提供程序模板](../../data/oledb/working-with-ole-db-provider-templates.md)