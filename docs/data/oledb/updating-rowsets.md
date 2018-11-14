---
title: 更新行集合
ms.date: 10/19/2018
helpviewer_keywords:
- rowsets, updating data
- updating data, rowsets
- updating rowsets
- rowsets
ms.assetid: 39588758-5c72-4254-a10d-cc2b1f473357
ms.openlocfilehash: d00b9036b216e3425615478d6bf92d239a3637d1
ms.sourcegitcommit: c40469825b6101baac87d43e5f4aed6df6b078f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/12/2018
ms.locfileid: "51556694"
---
# <a name="updating-rowsets"></a>更新行集合

基本数据库操作是更新，或将数据写入到数据存储区。 在 OLE DB 中，更新机制非常简单：使用者应用程序设置绑定数据成员的值，然后将这些值写入行集，然后使用者请求提供程序更新数据存储区。

使用者可以完成以下几种对行集数据的更新： 设置行中的列值、 插入的行和删除行。 若要完成这些操作，OLE DB 模板类[CRowset](../../data/oledb/crowset-class.md)实现[IRowsetChange](https://docs.microsoft.com/previous-versions/windows/desktop/ms715790(v=vs.85))接口并重写了以下接口方法：

- [SetData](../../data/oledb/crowset-setdata.md)更改列值的行集中某一行中; 它相当于 SQL UPDATE 命令。

- [插入](../../data/oledb/crowset-insert.md)将行插入到行; 它相当于 SQL INSERT 命令。

- [删除](../../data/oledb/crowset-delete.md)删除行集中的行; 它相当于 SQL DELETE 命令。

## <a name="supporting-update-operations"></a>支持更新操作

当您创建具有的使用者**ATL OLE DB 使用者向导**，您可以通过选择一个支持更新操作的详细信息的三个复选框**更改**，**插入**，并**删除**。 如果选择这些选项，该向导代码相应地修改以支持所选的更改类型。 但是，如果不使用该向导，您需要将以下行集属性设置为`VARIANT_TRUE`以支持更新：

- `DBPROPVAL_UP_CHANGE` 可以更改行中的数据值。

- `DBPROPVAL_UP_INSERT` 可以插入行。

- `DBPROPVAL_UP_DELETE` 使用此选项可删除的行。

按如下所示设置属性:

```cpp
CDBPropSet ps(DBPROPSET_ROWSET);

ps.AddProperty(DBPROP_IRowsetChange, true);
ps.AddProperty(DBPROP_UPDATABILITY, DBPROPVAL_UP_CHANGE | DBPROPVAL_UP_INSERT | DBPROPVAL_UP_DELETE);
```

如果一个或多个列不是可写的则更改、 插入或删除操作可能会失败。 修改光标映射以更正此问题。

## <a name="setting-data-in-rows"></a>设置行中的数据

[CRowset::SetData](../../data/oledb/crowset-setdata.md) 可设置当前行中一列或多列的数据值。 下面的代码设置绑定到列的数据成员的值`Name`并`Units in Stock`表的`Products`，然后调用`SetData`将这些值写入行集的第 100 行：

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

[CRowset::Insert](../../data/oledb/crowset-insert.md) 可使用取值函数中的数据创建并初始化新行。 `Insert` 在当前行; 后创建全新的行需要指定是当前到移到下一行还是保持其原来的位置。 通过设置 *bGetRow* 参数可以实现此操作：

```cpp
HRESULT Insert(int nAccessor = 0, bool bGetRow = false)
```

- **false** （默认值）指定将当前行移到下一行（以便指针指向插入的行）。

- **true**指定的当前行将保持其所在位置。

下面的代码设置绑定到表中的列的数据成员的值`Products`，然后调用`Insert`以行集的第 100 行之后插入具有这些值的新行。 建议设置所有列值以避免在新行中未定义的数据：

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

[CRowset::Delete](../../data/oledb/crowset-delete.md) 可删除行集中的当前行。 下面的代码调用`Delete`以删除行集中的第 100 行：

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

除非另外指定，否则，调用`SetData`， `Insert`，和`Delete`方法将立即更新数据存储区。 但是，也可以延迟更新，以便使用者将所有更改存储到本地缓存中，然后在调用以下其中一种更新方法时将这些更改传输到数据存储区：

- [CRowset::Update](../../data/oledb/crowset-update.md)传输任何挂起的更改对当前行进行自上次提取或`Update`对其调用。

- [CRowset::UpdateAll](../../data/oledb/crowset-updateall.md)传输任何挂起的更改对所有行进行自上次提取或`Update`对其调用。

更新与使用的更新方法，具有特定含义命令进行更改的和不使用 SQL 相混淆**更新**命令 (`SetData`等效于 SQL**更新**命令).

延迟的更新非常有用，例如，在一系列银行事务; 等情况如果一个事务已取消，您可以撤消更改，因为最后一个提交后，不要发送更改之前的一系列。 此外，提供程序还可将更改绑定到一个网络调用，这更加有效。

若要支持延迟的更新，必须设置`DBPROP_IRowsetChange`以及中所述的属性的属性**支持更新操作**:

```cpp
pPropSet->AddProperty(DBPROP_IRowsetUpdate, true);
```

当您调用`Update`或`UpdateAll`，方法将更改从本地缓存转移到数据存储，然后擦除本地缓存。 由于更新将仅对当前行的更改传输，务必，会跟踪你的应用程序的行更新以及何时更新它。 下面的示例演示如何更新两个连续的行：

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

若要确保传输挂起的更改，应调用`Update`移到另一行之前。 但是，如果非常繁琐或效率低下，例如当应用程序需要更新数百行时，则可以使用 `UpdateAll` 一次更新所有行。

例如，如果第一个`Update`调用上面的代码中缺失，第 100 行会保持不变，而第 101 行将更改。 稍后，你的应用程序必须调用`UpdateAll`或移回第 100 行并调用`Update`以更新该行。

最后，延迟更改的一个重要原因是能够撤消更改。 调用 [CRowset::Undo](../../data/oledb/crowset-undo.md) 会将本地更改缓存的状态回滚到进行任何挂起的更改之前数据存储区的状态。 务必要注意`Undo`不回滚的一个步骤 （最新的更改之前的状态） 的本地缓存的状态，相反，它将清除该行的本地缓存。 此外，`Undo`仅影响当前行。

## <a name="see-also"></a>请参阅

[使用 OLE DB 使用者模板](../../data/oledb/working-with-ole-db-consumer-templates.md)<br/>
[CRowset 类](../../data/oledb/crowset-class.md)<br/>
[IRowsetChange](https://docs.microsoft.com/previous-versions/windows/desktop/ms715790(v=vs.85))<br/>
