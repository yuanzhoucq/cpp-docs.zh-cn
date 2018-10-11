---
title: 更新行集合 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- rowsets, updating data
- updating data, rowsets
- updating rowsets
- rowsets
ms.assetid: 39588758-5c72-4254-a10d-cc2b1f473357
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: be82fb1c1f77ae3204bed54257062f362d286844
ms.sourcegitcommit: 3a141cf07b5411d5f1fdf6cf67c4ce928cf389c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/11/2018
ms.locfileid: "49083822"
---
# <a name="updating-rowsets"></a>更新行集合

一项非常基本的数据库操作是更新数据存储区中的数据或在其中写入数据。 在 OLE DB 中，更新机制非常简单：使用者应用程序设置绑定数据成员的值，然后将这些值写入行集，然后使用者请求提供程序更新数据存储区。  
  
使用者可以对行集数据执行以下几种更新：设置行内的列值、插入行以及删除行。 为了执行这些操作，OLE DB 模板类 [CRowset](../../data/oledb/crowset-class.md) 实现了 [IRowsetChange](/previous-versions/windows/desktop/ms715790) 接口并重写了以下接口方法：  
  
- [SetData](../../data/oledb/crowset-setdata.md) 可更改行集中某一行内的列值；它等效于 SQL UPDATE 命令。  
  
- [Insert](../../data/oledb/crowset-insert.md) 可在行集内插入一行；它等效于 SQL INSERT 命令。  
  
- [Delete](../../data/oledb/crowset-delete.md) 可删除行集中的行；它等效于 SQL DELETE 命令。  
  
## <a name="supporting-update-operations"></a>支持更新操作  

使用“ATL OLE DB 使用者向导”创建使用者时，可以支持更新操作，方法是选中“更改” 、“插入” 以及“删除” 这三个复选框中的一个或多个。 如果选中这些复选框，则向导将相应地修改代码，以支持你选定的更改类型。 但是，如果不使用该向导，则需要将以下行集属性设置为 `VARIANT_TRUE` 以支持更新：  
  
- `DBPROPVAL_UP_CHANGE` 可以更改行中的数据值。  
  
- `DBPROPVAL_UP_INSERT` 可以插入行。  
  
- `DBPROPVAL_UP_DELETE` 使用此选项可删除的行。  
  
按如下所示设置属性:  
  
```cpp  
CDBPropSet ps(DBPROPSET_ROWSET);  

ps.AddProperty(DBPROP_IRowsetChange, true)  
ps.AddProperty(DBPROP_UPDATABILITY, DBPROPVAL_UP_CHANGE | DBPROPVAL_UP_INSERT | DBPROPVAL_UP_DELETE)  
```  
  
如果一列或多列不可写，则更改、插入或删除操作可能失败。 修改光标映射以更正此问题。  
  
## <a name="setting-data-in-rows"></a>设置行中的数据  

[CRowset::SetData](../../data/oledb/crowset-setdata.md) 可设置当前行中一列或多列的数据值。 下面的代码用于设置绑定到 Products 表中“Name”和“Units in Stock”列的数据成员的值，然后调用 `SetData` 以将这些值写入行集的第 100 行：  
  
```cpp  
// Instantiate a rowset based on the user record class  
CTable<CAccessor<CProductAccessor>> product;  
CSession session;  
  
// Open the rowset and move to the 100th row  
product.Open(session, "Product", &ps, 1);  // ps is the property set  
product.MoveToBookmark(&bookmark, 0);      // Assume that bookmark is set to 100th row  
  
// Change the values of columns "Name" and "Units in Stock" in the current row of the Product table  
_tcscpy_s(product.m_ProductName, product.m_sizeOfProductName,  
           _T( "Candle" ) );  

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
  
- **true** 指定当前行保留其原来的位置。  
  
下面的代码将绑定到 Products 表的列的数据成员的值，然后调用`Insert`以行集的第 100 行之后插入具有这些值的新行。 建议设置所有列值，以避免新行中存在未定义的数据：  
  
```cpp  
// Instantiate a rowset based on the user record class  
CTable<CAccessor<CProductAccessor>> product;  
CSession session;  
  
// Open the rowset and move to the 100th row  
product.Open(session, "Product", &ps, 1);  // ps is the property set  
product.MoveToBookmark(&bookmark, 0);      // Assume that bookmark is set to 100th row  
  
// Set the column values for a row of the Product table, then insert the row  
product.m_ProductID = 101;  
_tcscpy_s(product.m_ProductName, product.m_sizeOfProductName,  
           _T( "Candle" ) );  

product.m_SupplierID = 27857;  
product.m_CategoryID = 372;  
_tcscpy_s(product.m_QuantityPerUnit, product.m_sizeOfQuantityPerUnit,  
           _T( "Pack of 10" ) );  

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
  
注意，使用 Update 方法实现的更新具有特定的更改含义，且不易与 SQL UPDATE 命令混淆（`SetData` 等效于 SQL UPDATE 命令。）  
  
延迟更新非常有用，例如在进行一系列银行事务的情况下；如果取消了一项事务，则可以撤消更改，因为只有在提交了上一个更改后才会发送后面的更改。 此外，提供程序还可将更改绑定到一个网络调用，这更加有效。  
  
若要支持延迟的更新，必须设置`DBPROP_IRowsetChange`属性以及"支持更新操作"中所述的属性：  
  
```cpp  
pPropSet->AddProperty(DBPROP_IRowsetUpdate, true);  
```  
  
当您调用`Update`或`UpdateAll`，方法将更改从本地缓存转移到数据存储，然后擦除本地缓存。 由于更新将仅传输当前行的更改，因此应用程序必须跟踪要更新的行以及更新时间。 下面的示例演示如何更新两个连续的行：  
  
```cpp  
// Instantiate a rowset based on the user record class  
CTable<CAccessor<CProductAccessor>> product;  
CSession session;  
  
// Open the rowset and move to the 100th row  
product.Open(session, "Product", &ps, 1);  // ps is the property set  
product.MoveToBookmark(&bookmark, 0);      // Assume that bookmark is set to 100th row  
  
// Change the values of columns "Name" and "Units in Stock" in the 100th row of the Product table  
_tcscpy_s(product.m_ProductName, product.m_sizeOfProductName,  
           _T( "Wick" ) );  

product.m_UnitsInStock = 10000;  

HRESULT hr = product.SetData();  // No changes made to row 100 yet  
product.Update();                 // Update row 100 now  
  
// Change the values of columns "Name" and "Units in Stock" in the 101st row of the Product table  
product.MoveNext();  

_tcscpy_s(product.m_ProductName, product.m_sizeOfProductName  
           _T( "Wax" ) );  

product.m_UnitsInStock = 500;  

HRESULT hr = product.SetData();  // No changes made to row 101 yet  
product.Update();                 // Update row 101 now  
```  
  
若要确保传输挂起的更改，应调用`Update`移到另一行之前。 但是，如果非常繁琐或效率低下，例如当应用程序需要更新数百行时，则可以使用 `UpdateAll` 一次更新所有行。  
  
例如，如果第一个`Update`调用上面的代码中缺失，100 行将保持不变，而第 101 行将更改。 稍后，你的应用程序必须调用`UpdateAll`或移回第 100 行并调用`Update`以更新该行。  
  
最后，延迟更改的一个重要原因是能够撤消更改。 调用 [CRowset::Undo](../../data/oledb/crowset-undo.md) 会将本地更改缓存的状态回滚到进行任何挂起的更改之前数据存储区的状态。 务必要注意`Undo`不会回滚的一个步骤 （最新的更改之前的状态） 的本地缓存的状态，相反，它将清除该行的本地缓存。 此外，`Undo`仅影响当前行。  
  
## <a name="see-also"></a>请参阅  

[使用 OLE DB 使用者模板](../../data/oledb/working-with-ole-db-consumer-templates.md)<br/>
[CRowset 类](../../data/oledb/crowset-class.md)<br/>
[IRowsetChange](/previous-versions/windows/desktop/ms715790)