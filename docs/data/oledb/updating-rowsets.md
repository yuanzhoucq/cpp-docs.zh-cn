---
title: 更新行集合
ms.date: 05/09/2019
helpviewer_keywords:
- rowsets, updating data
- updating data, rowsets
- updating rowsets
- rowsets
ms.assetid: 39588758-5c72-4254-a10d-cc2b1f473357
ms.openlocfilehash: e0ee5cf97170cd9293abcb9039771f8fe23962aa
ms.sourcegitcommit: 00e26915924869cd7eb3c971a7d0604388abd316
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/10/2019
ms.locfileid: "65525304"
---
# <a name="updating-rowsets"></a>更新行集合

一项基本数据库操作是，更新数据存储或向其中写入数据。 在 OLE DB 中，更新机制非常简单：使用者应用程序设置绑定数据成员的值，然后将这些值写入行集，然后使用者请求提供程序更新数据存储区。

使用者可以对行集数据完成以下几种更新：设置行内的列值、插入行以及删除行。 为了完成这些操作，OLE DB 模板类 [CRowset](../../data/oledb/crowset-class.md) 实现 [IRowsetChange](/previous-versions/windows/desktop/ms715790(v=vs.85)) 接口，并重写以下接口方法：

- [SetData](../../data/oledb/crowset-setdata.md)：更改行集中某一行内的列值；它相当于 SQL UPDATE 命令。

- [Insert](../../data/oledb/crowset-insert.md)：在行集内插入行；它相当于 SQL INSERT 命令。

- [Delete](../../data/oledb/crowset-delete.md)：删除行集中的行；它相当于 SQL DELETE 命令。

## <a name="supporting-update-operations"></a>支持更新操作

> [!NOTE]
> ATL OLE DB 使用者向导不适用于 Visual Studio 2019 及更高版本。 但仍可以手动添加此功能。 有关详细信息，请参阅[不使用向导创建使用者](creating-a-consumer-without-using-a-wizard.md)。

使用 ATL OLE DB 使用者向导创建使用者时，可以选中“更改”、“插入”和“删除”这三个复选框中的一个或多个来支持更新操作。 如果你选中这些选项，向导会将代码相应修改为支持你选择的更改类型。 不过，如果不使用向导，必须将以下行集属性设置为 `VARIANT_TRUE`，才能支持更新：

- `DBPROPVAL_UP_CHANGE`：允许更改行内的数据值。

- `DBPROPVAL_UP_INSERT`：允许插入行。

- `DBPROPVAL_UP_DELETE`：允许删除行。

按如下所示设置属性:

```cpp
CDBPropSet ps(DBPROPSET_ROWSET);

ps.AddProperty(DBPROP_IRowsetChange, true);
ps.AddProperty(DBPROP_UPDATABILITY, DBPROPVAL_UP_CHANGE | DBPROPVAL_UP_INSERT | DBPROPVAL_UP_DELETE);
```

如果一个或多个列不可写，那么更改、插入或删除操作可能会失败。 若要更正此问题，请修改光标映射。

## <a name="setting-data-in-rows"></a>设置行中的数据

[CRowset::SetData](../../data/oledb/crowset-setdata.md) 可设置当前行中一列或多列的数据值。 下面的代码设置绑定到表 `Products` 中列 `Name` 和 `Units in Stock` 的数据成员的值，然后调用 `SetData` 将这些值写入行集的第 100 行：

```cpp
// Instantiate a rowset based on the user record class
CTable<CAccessor<CProductAccessor>> product;
CSession session;

// Open the rowset and move to the 100th row
product.Open(session, "Product", &ps, 1);  // ps is the property set
product.MoveToBookmark(&bookmark, 0);      // Assume that bookmark is set to 100th row

// Change the values of columns "Name" and "Units in Stock" in the current row of the Product table
_tcscpy_s(product.m_ProductName, product.m_sizeOfProductName, _T( "Candle" ) );

product.m_UnitsInStock = 10000;

// Set the data
HRESULT hr = product.SetData();
```

## <a name="inserting-rows-into-rowsets"></a>在行集中插入行

[CRowset::Insert](../../data/oledb/crowset-insert.md) 可使用取值函数中的数据创建并初始化新行。 `Insert` 在当前行后面创建一个全新的行；你需要指定是将当前行递增到下一行，还是保持原来位置不变。 通过设置 *bGetRow* 参数可以实现此操作：

```cpp
HRESULT Insert(int nAccessor = 0, bool bGetRow = false)
```

- **false** （默认值）指定将当前行移到下一行（以便指针指向插入的行）。

- true 指定当前行保持原来位置不变。

下面的代码设置绑定到表 `Products` 中列的数据成员的值，然后调用 `Insert` 在行集的第 100 行后面插入包含这些值的新行。 建议设置所有列值，以免新行中出现未定义的数据：

```cpp
// Instantiate a rowset based on the user record class
CTable<CAccessor<CProductAccessor>> product;
CSession session;

// Open the rowset and move to the 100th row
product.Open(session, "Product", &ps, 1);  // ps is the property set
product.MoveToBookmark(&bookmark, 0);      // Assume that bookmark is set to 100th row

// Set the column values for a row of the Product table, then insert the row
product.m_ProductID = 101;
_tcscpy_s(product.m_ProductName, product.m_sizeOfProductName, _T( "Candle" ) );

product.m_SupplierID = 27857;
product.m_CategoryID = 372;
_tcscpy_s(product.m_QuantityPerUnit, product.m_sizeOfQuantityPerUnit, _T( "Pack of 10" ) );

product.m_UnitPrice = 20;
product.m_UnitsInStock = 10000;
product.m_UnitsOnOrder = 5201;
product.m_ReorderLevel = 5000;
product.m_Discontinued = false;

// You must also initialize the status and length fields before setting/inserting data
// Set the column status values
m_dwProductIDStatus = DBSTATUS_S_OK;
m_dwProductNameStatus = DBSTATUS_S_OK;
m_dwSupplierIDStatus = DBSTATUS_S_OK;
m_dwCategoryIDStatus = DBSTATUS_S_OK;
m_dwQuantityPerUnitStatus = DBSTATUS_S_OK;
m_dwUnitPriceStatus = DBSTATUS_S_OK;
m_dwUnitsInStockStatus = DBSTATUS_S_OK;
m_dwUnitsOnOrderStatus = DBSTATUS_S_OK;
m_dwReorderLevelStatus = DBSTATUS_S_OK;
m_dwDiscontinuedStatus = DBSTATUS_S_OK;

// Set the column length value for column data members that are not fixed-length types.
// The value should be the length of the string that you are setting.
m_dwProductNameLength = 6;             // "Candle" has 6 characters
m_dwQuantityPerUnitLength = 10;        // "Pack of 10" has 10 characters

// Insert the data
HRESULT hr = product.Insert();
```

有关更详细的示例，请参阅 [CRowset::Insert](../../data/oledb/crowset-insert.md)。

有关设置状态和长度数据成员的详细信息，请参阅 [向导生成的取值函数中的字段状态数据成员](../../data/oledb/field-status-data-members-in-wizard-generated-accessors.md)。

## <a name="deleting-rows-from-rowsets"></a>删除行集中的行

[CRowset::Delete](../../data/oledb/crowset-delete.md) 可删除行集中的当前行。 下面的代码调用 `Delete` 来删除行集的第 100 行：

```cpp
// Instantiate a rowset based on the user record class
CTable<CAccessor<CProductAccessor>> product;
CSession session;

// Open the rowset and move to the 100th row
product.Open(session, "Product", &ps, 1);  // ps is the property set
product.MoveToBookmark(&bookmark, 0);      // Assume that bookmark is set to 100th row

// Delete the row
HRESULT hr = product.Delete();
```

## <a name="immediate-and-deferred-updates"></a>立即和延迟更新

除非另有说明，否则调用 `SetData`、`Insert` 和 `Delete` 方法会立即更新数据存储。 但是，也可以延迟更新，以便使用者将所有更改存储到本地缓存中，然后在调用以下其中一种更新方法时将这些更改传输到数据存储区：

- [CRowset::Update](../../data/oledb/crowset-update.md)：传输自上次提取或对它调用 `Update` 后，对当前行进行的任何挂起的更改。

- [CRowset::UpdateAll](../../data/oledb/crowset-updateall.md)：传输自上次提取或对它调用 `Update` 后，对所有行进行的任何挂起的更改。

更新方法中使用的 Update 对于更改命令有特定的含义，不要与 SQL UPDATE 命令混淆（`SetData` 相当于 SQL UPDATE 命令）。

延迟更新非常有用，例如在进行一系列银行交易的情况下；如果一项交易已取消，你可以撤消更改，因为只有在提交了上一个更改后才会发送一系列更改。 此外，提供程序还可将更改绑定到一个网络调用，这更加有效。

若要支持延迟更新，必须设置 `DBPROP_IRowsetChange` 属性，以及“支持更新操作”中介绍的属性：

```cpp
pPropSet->AddProperty(DBPROP_IRowsetUpdate, true);
```

如果你调用 `Update` 或 `UpdateAll`，这些方法会将本地缓存中的更改传输到数据存储，然后擦除掉本地缓存。 由于更新仅传输当前行的更改，因此应用程序必须跟踪要更新的行以及更新时间。 下面的示例演示如何更新两个连续的行：

```cpp
// Instantiate a rowset based on the user record class
CTable<CAccessor<CProductAccessor>> product;
CSession session;

// Open the rowset and move to the 100th row
product.Open(session, "Product", &ps, 1);  // ps is the property set
product.MoveToBookmark(&bookmark, 0);      // Assume that bookmark is set to 100th row

// Change the values of columns "Name" and "Units in Stock" in the 100th row of the Product table
_tcscpy_s(product.m_ProductName, product.m_sizeOfProductName, _T( "Wick" ) );

product.m_UnitsInStock = 10000;

HRESULT hr = product.SetData();  // No changes made to row 100 yet
product.Update();                 // Update row 100 now

// Change the values of columns "Name" and "Units in Stock" in the 101st row of the Product table
product.MoveNext();

_tcscpy_s(product.m_ProductName, product.m_sizeOfProductName _T( "Wax" ) );

product.m_UnitsInStock = 500;

HRESULT hr = product.SetData();  // No changes made to row 101 yet
product.Update();                 // Update row 101 now
```

为了确保传输挂起的更改，应先调用 `Update`，再移到另一行。 但是，如果非常繁琐或效率低下，例如当应用程序需要更新数百行时，则可以使用 `UpdateAll` 一次更新所有行。

例如，如果上面的代码中缺少 `Update` 调用，那么第 100 行保持不变，而第 101 行则更改。 稍后，应用程序必须调用 `UpdateAll` 或移回第 100 行并调用 `Update`，才能更新此行。

最后，延迟更改的一个重要原因是能够撤消更改。 调用 [CRowset::Undo](../../data/oledb/crowset-undo.md) 会将本地更改缓存的状态回滚到进行任何挂起的更改之前数据存储区的状态。 请务必注意，`Undo` 不会将本地存储的状态回滚一步（即仅在最新更改之前的状态），而是清除相应行的本地缓存。 此外，`Undo` 只影响当前行。

## <a name="see-also"></a>请参阅

[使用 OLE DB 使用者模板](../../data/oledb/working-with-ole-db-consumer-templates.md)<br/>
[CRowset 类](../../data/oledb/crowset-class.md)<br/>
[IRowsetChange](/previous-versions/windows/desktop/ms715790(v=vs.85))<br/>
