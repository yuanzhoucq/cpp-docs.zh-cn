---
title: 记录集：动态绑定数据列 (ODBC)
ms.date: 11/19/2018
helpviewer_keywords:
- ODBC recordsets [C++], binding columns dynamically
- data binding [C++], recordset columns
- recordsets [C++], binding data
- data binding [C++], columns in recordsets
- columns [C++], binding to recordsets
ms.assetid: bff67254-d953-4ae4-9716-91c348cb840b
ms.openlocfilehash: c2f2a6a6696f46fb5b8f2777c6c911269c9e7a80
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "59035113"
---
# <a name="recordset-dynamically-binding-data-columns-odbc"></a>记录集：动态绑定数据列 (ODBC)

本主题适用于 MFC ODBC 类。

记录集管理在设计时指定的绑定列，但有些情况下你可能想要将列在设计时是未知的绑定。 本主题说明：

- [当你可能想要动态将列绑定到记录集](#_core_when_you_might_bind_columns_dynamically)。

- [如何在运行时动态绑定列](#_core_how_to_bind_columns_dynamically)。

> [!NOTE]
>  本主题适用于对象派生自`CRecordset`中的批量行提取尚未实现。 如果使用批量行提取，不建议通常所述的技术。 有关批量行提取的详细信息，请参阅[记录集：(ODBC) 批量提取记录](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

##  <a name="_core_when_you_might_bind_columns_dynamically"></a> 当可能动态绑定列

在设计时，MFC 应用程序向导或[MFC ODBC 使用者向导](../../mfc/reference/adding-an-mfc-odbc-consumer.md)(从**添加类**) 创建基于已知的表和列对数据源的记录集类。 数据库可以设计并随后在您的应用程序在运行时使用这些表和列时之间进行更改。 你或其他用户可能会添加或删除的表或添加或删除从应用程序的记录集所依赖的表中的列。 这可能并不是问题的所有数据访问应用程序，但如果它对您，可以解决与数据库架构，而通过重新设计并重新编译中的更改？ 本主题的目的是要回答这个问题。

本主题介绍可能会动态绑定列的最常见情况 — 具有已开始基于已知的数据库架构的记录集，想要在运行时处理其他的列。 本主题进一步假定其他列将映射到`CString`字段数据成员，最常见的情况，但也提供建议来帮助你管理其他数据类型。

使用少量的额外代码，你可以：

- [确定在运行时可用的哪些列](#_core_how_to_bind_columns_dynamically)。

- [其他动态将列绑定到记录集，在运行时](#_core_adding_the_columns)。

记录集仍包含在设计时知道此信息的列的数据成员。 它还包含少量额外代码来动态确定任何新列是否已添加到目标表，并且如果是这样，这些新列绑定到动态分配的存储 （而不是记录集数据成员）。

本主题不涉及其他动态绑定的情况下，如删除的表或列。 对于这些情况下，需要更直接地使用 ODBC API 调用。 有关信息，请参阅 ODBC SDK*程序员参考*MSDN 库 CD 上。

##  <a name="_core_how_to_bind_columns_dynamically"></a> 如何动态绑定列

若要动态绑定列，您必须知道 （或能够确定） 的其他列的名称。 此外必须分配存储空间的其他字段数据成员，指定其名称和类型，并指定要添加的列数。

下面的讨论涉及两个不同的记录集。 首先，从目标表中选择记录的主要记录集。 第二个是用于获取目标表中的列信息的特殊列记录集。

###  <a name="_core_the_general_process"></a> 常规过程

最常规的级别，则请执行以下步骤：

1. 构建主要记录集对象。

   （可选） 将指针传递到一种开放`CDatabase`对象或必须能够连接信息提供给列记录集以某种其他方式。

1. 采取措施以动态方式添加列。

   请参阅添加下面的列中所述的过程。

1. 打开主要记录集。

   记录集选择记录，并使用记录字段交换 (RFX) 将静态列 （映射到记录集字段数据成员） 和 （映射到分配的额外存储） 的动态列绑定。

###  <a name="_core_adding_the_columns"></a> 添加列

动态绑定添加在运行时列需要执行以下步骤：

1. 在运行时确定的目标表中包括的列。 从该信息提取由于记录集类专门已添加到表的列的列表。

   一个不错的方法是使用而设计来查询数据源 （例如列名和数据类型） 的目标表的列信息的列记录集类。

1. 为新的字段数据成员提供存储。 因为您主要记录集的类不具有未知的列的字段数据成员，必须提供一个位置来存储名称、 结果值和可能的数据类型信息 （如果这些列是不同的数据类型）。

   一种方法是生成一个或多个动态列表，一个用于新列的名称，另一个用于其结果值，并为其数据类型第三个 （如有必要）。 这些列表，特别是值列表中，提供的信息并绑定必要的存储。 下图演示如何生成列表。

   ![生成要动态绑定列的列表](../../data/odbc/media/vc37w61.gif "生成要动态绑定列的列表")<br/>
   生成要动态绑定的列列表

1. 在主要记录集的添加 RFX 函数调用`DoFieldExchange`函数为每个已添加列。 这些 RFX 调用执行提取一条记录，包括其他列，以及它们将列绑定为到记录集数据成员或动态提供存储的工作。

   一种方法是向主要记录集的添加循环`DoFieldExchange`循环访问新列，对于列表中每个列调用相应的 RFX 函数的列表的函数。 每个 RFX 调用时，将从列名称列表和相应成员的结果值列表中的存储位置传递列名称。

###  <a name="_core_lists_of_columns"></a> 列的列表

下表中显示需要使用的四个列表。

|||
|-|-|
|**Current-Table-Columns**| （图中的列表 1）在数据源的表中当前列的列表。 此列表可能与匹配的记录集中当前绑定的列的列表。|
|**Bound-Recordset-Columns**| （图中的列表 2）记录集中绑定列的列表。 这些列中已有 RFX 语句在`DoFieldExchange`函数。|
|**列-到-动态绑定**| （图中的列表 3）列的表中但不是在记录集的列表。 下面是你想要动态绑定的列。|
|**Dynamic-Column-Values**| （图中的列表 4）从动态绑定列中检索包含存储的值的列表。 此列表的元素与中的列-到-动态绑定，一相对应。|

###  <a name="_core_building_your_lists"></a> 构建您的列表

记住的常规策略，就可以开始的详细信息。 本主题的其余部分中的过程演示如何生成列表中所示[的列列表](#_core_lists_of_columns)。 过程将指导你完成：

- [确定不在记录集中的列的名称](#_core_determining_which_table_columns_are_not_in_your_recordset)。

- [为列添加到表中新提供动态存储](#_core_providing_storage_for_the_new_columns)。

- [为新列中动态添加 RFX 调用](#_core_adding_rfx_calls_to_bind_the_columns)。

###  <a name="_core_determining_which_table_columns_are_not_in_your_recordset"></a> 确定哪些表的列未处于记录集

生成包含已绑定主记录集中的列的列表的列表 （绑定记录集列，如图中的列表 2 中所示）。 然后生成 （列-到-动态绑定，派生表的当前列和记录集的绑定列） 包含在数据源的表中而不是在主记录集中的列名称的列表。

##### <a name="to-determine-the-names-of-columns-not-in-the-recordset-columns-to-bind-dynamically"></a>若要确定不在记录集 （-绑定的动态列） 中列的名称

1. 生成的主记录集已绑定的列的列表 （绑定记录集列）。

   一种方法是在设计时创建记录集的绑定列。 您可以直观地检查 RFX 函数调用在记录集的`DoFieldExchange`函数以获取这些名称。 然后，将列表设置为使用名称初始化的数组。

   例如，图显示了具有三个元素的绑定的记录集的列 (列表 2)。 记录集的绑定列缺少电话列在当前表列 (列表 1) 中所示。

1. 比较表的当前列和记录集的绑定列来生成 （-绑定的动态列） 的主记录集中尚不存在绑定的列的列表。

   一种方法是在运行的时 （当前表列） 和在列列表的已记录集中绑定 （绑定记录集列） 在并行循环访问表中的列的列表。 列-到-动态绑定到当前--在表列中不出现在记录集的绑定列放置的任何名称。

   例如，图显示了列-到-动态绑定 (列表 3) 与一个元素： 出现在当前表列 (列表 1) 中，但不是在绑定记录集列 (列表 2) 的 Phone 列。

1. 要在其中存储对应于每个列名称存储在要动态绑定的列列表中 （列-到-动态绑定） 的数据值生成的动态列的值 （如图中的列表 4) 的列表。

   此列表的元素的作用是新的记录集字段数据成员。 它们是动态列绑定到的存储位置。 有关列表的说明，请参阅[的列列表](#_core_lists_of_columns)。

###  <a name="_core_providing_storage_for_the_new_columns"></a> 提供的新列用于存储空间

接下来，设置要动态绑定的列的存储位置。 旨在提供一个列表元素用来存储每个列的值。 这些存储位置的并行存储通常绑定的列的记录集成员变量。

#### <a name="to-provide-dynamic-storage-for-new-columns-dynamic-column-values"></a>若要为新列 （动态列值） 提供动态存储

1. 生成动态列的值，平行的列-到-动态绑定，使其包含的每个列中的数据值。

   例如，图中显示动态列值 (列表 4) 了其中一个元素：`CString`对象，其中包含当前记录的实际电话号码："555-1212".

   在最常见的情况下，列的动态值具有类型元素的`CString`。 如果处理的不同数据类型的列，则需要一个列表，其中可以包含各种类型的元素。

前面的过程的结果是两个主要的列表：列-到-包含要动态绑定列和动态列的值包含当前记录的列中的值的名称。

> [!TIP]
> 如果新列不是所有相同的数据类型，可能需要一个额外的并行列表包含以某种方式定义的每个相应元素的类型的列列表中的项。 （可以使用值 AFX_RFX_BOOL，AFX_RFX_BYTE，并在其他方面，此 if 所需。 这些常量 AFXDB 中定义。H.)选择基于表示列数据类型的方式的列表类型。

###  <a name="_core_adding_rfx_calls_to_bind_the_columns"></a> 添加 RFX 调用将列绑定

最后，排列为动态绑定上来将发生的新列中的 RFX 调用你`DoFieldExchange`函数。

##### <a name="to-dynamically-add-rfx-calls-for-new-columns"></a>若要动态添加新列的 RFX 调用

1. 在主要记录集的`DoFieldExchange`成员函数中，添加代码以循环遍历新列 （列-到-动态绑定） 的列表。 在每个循环中，从列-到-动态绑定和中列的动态值的列的结果值中提取的列名称。 这些将项传递到 RFX 函数调用适用于列的数据类型。 有关列表的说明，请参阅[的列列表](#_core_lists_of_columns)。

通常情况下中, 您`RFX_Text`函数的调用您提取`CString`对象从在列表中，如以下代码，其中的绑定的动态列是行中所示`CStringList`调用`m_listName`和动态列值是`CStringList`调用`m_listValue`:

```cpp
RFX_Text( pFX,
            m_listName.GetNext( posName ),
            m_listValue.GetNext( posValue ));
```

有关 RFX 函数的详细信息，请参阅[宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)中*类库参考*。

> [!TIP]
> 如果新列是不同的数据类型，使用 switch 语句在循环中为每个类型调用相应的 RFX 函数。

当框架将调用`DoFieldExchange`期间`Open`过程以将列绑定到记录集，RFX 调用，对于静态列，则绑定这些列。 然后在循环重复调用 RFX 函数的动态列。

## <a name="see-also"></a>请参阅

[记录集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[记录集：处理大数据项 (ODBC)](../../data/odbc/recordset-working-with-large-data-items-odbc.md)