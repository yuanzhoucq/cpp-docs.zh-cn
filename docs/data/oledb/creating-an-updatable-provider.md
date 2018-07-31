---
title: 创建可更新的提供程序 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, updatable
- notifications, support in providers
- OLE DB providers, creating
ms.assetid: bdfd5c9f-1c6f-4098-822c-dd650e70ab82
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e9ee36d2300ed1e86c1f867012ed54c85692f5bd
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/30/2018
ms.locfileid: "39340633"
---
# <a name="creating-an-updatable-provider"></a>创建可更新的提供程序

Visual c + + 支持可更新的提供程序或可更新的提供程序 （写入） 数据存储区。 本主题讨论如何创建可更新的提供程序使用 OLE DB 模板。  
  
 本主题假定你着手工作提供程序。 有两个步骤创建可更新的提供程序。 您必须首先确定如何提供程序将对数据存储区; 进行的更改具体而言，是否更改会立即完成或者延迟，直到发出 update 命令。 部分"[使提供程序可更新](#vchowmakingprovidersupdatable)"的更改和的设置，需要在提供程序代码中执行操作。  
  
 接下来，必须确保您的提供程序包含所有功能，以支持使用者可能会请求它的任何内容。 如果使用者想要更新的数据存储区，则提供程序必须包含的数据保存到数据存储区的代码。 例如，可能会使用 MFC 的 C 运行时库来执行此类操作对数据源。 部分"[写入到数据源](#vchowwritingtothedatasource)"介绍如何将写入到数据源，处理 NULL 和默认值，并设置列标志。  
  
> [!NOTE]
>  UpdatePV 是可更新的提供程序的示例。 UpdatePV 是相同的作为 MyProv 但对可更新的支持。  
  
##  <a name="vchowmakingprovidersupdatable"></a> 使提供程序可更新  

 使提供程序可更新的关键了解您希望在提供程序对数据存储区和想要执行这些操作的提供程序如何执行哪些的操作。 具体而言，主要问题是数据存储区的更新是否要立即完成或延迟 （批处理） 发出更新命令之前。  
  
 您必须首先决定是否继承自`IRowsetChangeImpl`或`IRowsetUpdateImpl`行集类中。 具体取决于这些所选内容来实现，三种方法的功能将会受到影响： `SetData`， `InsertRows`，和`DeleteRows`。  
  
- 如果继承自[IRowsetChangeImpl](../../data/oledb/irowsetchangeimpl-class.md)，立即调用这三种方法更改数据存储区。  
  
- 如果继承自[IRowsetUpdateImpl](../../data/oledb/irowsetupdateimpl-class.md)，方法延迟到数据存储区的更改，直到你调用`Update`， `GetOriginalData`，或`Undo`。 如果更新涉及多项更改，它们在批处理模式下 （请注意，批处理更改可以添加相当大的内存开销） 执行。  
  
 请注意，`IRowsetUpdateImpl`派生自`IRowsetChangeImpl`。 因此，`IRowsetUpdateImpl`提供更改功能以及批处理功能。  
  
#### <a name="to-support-updatability-in-your-provider"></a>若要在您的提供程序中支持可更新性  
  
1. 在行集类中，继承自`IRowsetChangeImpl`或`IRowsetUpdateImpl`。 这些类用于更改数据存储区提供相应的接口：  
  
     **添加 IRowsetChange**  
  
     添加`IRowsetChangeImpl`到使用此窗体继承链：  
  
    ```cpp  
    IRowsetChangeImpl< rowset-name, storage-name >  
    ```  
  
     此外将添加`COM_INTERFACE_ENTRY(IRowsetChange)`到`BEGIN_COM_MAP`行集类中的部分。  
  
     **添加 IRowsetUpdate**  
  
     添加`IRowsetUpdate`到使用此窗体继承链：  
  
    ```cpp  
    IRowsetUpdateImpl< rowset-name, storage>  
    ```  
  
    > [!NOTE]
    >  应删除`IRowsetChangeImpl`继承链中的行。 如前面所述的指令的此例外必须包含的代码`IRowsetChangeImpl`。  
  
2.  将以下代码添加到 COM 映射 (`BEGIN_COM_MAP ... END_COM_MAP`):  
  
    |如果你实现|将添加到 COM 映射|  
    |----------------------|--------------------|  
    |`IRowsetChangeImpl`|`COM_INTERFACE_ENTRY(IRowsetChange)`|  
    |`IRowsetUpdateImpl`|`COM_INTERFACE_ENTRY(IRowsetChange)COM_INTERFACE_ENTRY(IRowsetUpdate)`|  
  
3.  在命令中，将以下代码添加到属性集映射中 (`BEGIN_PROPSET_MAP ... END_PROPSET_MAP`):  
  
    |如果你实现|将添加到属性组映射|  
    |----------------------|-----------------------------|  
    |`IRowsetChangeImpl`|`PROPERTY_INFO_ENTRY_VALUE(IRowsetChange, VARIANT_FALSE)`|  
    |`IRowsetUpdateImpl`|`PROPERTY_INFO_ENTRY_VALUE(IRowsetChange, VARIANT_FALSE)PROPERTY_INFO_ENTRY_VALUE(IRowsetUpdate, VARIANT_FALSE)`|  
  
4.  在属性集映射中，您还应包括以下设置的所有按照如下所示：  
  
    ```cpp  
    PROPERTY_INFO_ENTRY_VALUE(UPDATABILITY, DBPROPVAL_UP_CHANGE |   
      DBPROPVAL_UP_INSERT | DBPROPVAL_UP_DELETE)  
    PROPERTY_INFO_ENTRY_VALUE(CHANGEINSERTEDROWS, VARIANT_TRUE)  
    PROPERTY_INFO_ENTRY_VALUE(IMMOBILEROWS, VARIANT_TRUE)  
  
    PROPERTY_INFO_ENTRY_EX(OWNINSERT, VT_BOOL, DBPROPFLAGS_ROWSET |   
      DBPROPFLAGS_READ, VARIANT_TRUE, 0)  
    PROPERTY_INFO_ENTRY_EX(OWNUPDATEDELETE, VT_BOOL, DBPROPFLAGS_ROWSET |   
      DBPROPFLAGS_READ, VARIANT_TRUE, 0)  
    PROPERTY_INFO_ENTRY_EX(OTHERINSERT, VT_BOOL, DBPROPFLAGS_ROWSET |   
      DBPROPFLAGS_READ, VARIANT_TRUE, 0)  
    PROPERTY_INFO_ENTRY_EX(OTHERUPDATEDELETE, VT_BOOL, DBPROPFLAGS_ROWSET |   
      DBPROPFLAGS_READ, VARIANT_TRUE, 0)  
    PROPERTY_INFO_ENTRY_EX(REMOVEDELETED, VT_BOOL, DBPROPFLAGS_ROWSET |   
      DBPROPFLAGS_READ, VARIANT_FALSE, 0)  
    ```  
  
     您可以找到这些宏调用中，由在 Atldb.h 中查找的属性 Id 和值的值 （如果 Atldb.h 不同于联机文档，Atldb.h 取代文档）。  
  
    > [!NOTE]
    >  许多`VARIANT_FALSE`和`VARIANT_TRUE`设置所需的 OLE DB 模板; OLE DB 规范指出，它们可以是读/写，但 OLE DB 模板仅支持一个值。  
  
     **如果实现 IRowsetChangeImpl**  
  
     如果你实现`IRowsetChangeImpl`，必须在您的提供程序上设置以下属性。 这些属性主要用于请求通过接口`ICommandProperties::SetProperties`。  
  
    - `DBPROP_IRowsetChange`： 设置将自动设置`DBPROP_IRowsetChange`。  
  
    - `DBPROP_UPDATABILITY`： 指定受支持的方法一个位掩码`IRowsetChange`: `SetData`， `DeleteRows`，或`InsertRow`。  
  
    - `DBPROP_CHANGEINSERTEDROWS`： 使用者可以调用`IRowsetChange::DeleteRows`或`SetData`为新插入的行。  
  
    - `DBPROP_IMMOBILEROWS`： 行集不会对插入或更新的行重新排序。  
  
     **如果实现 IRowsetUpdateImpl**  
  
     如果你实现了`IRowsetUpdateImpl`，必须设置以下属性上您的提供商，除了为的所有属性都设置`IRowsetChangeImpl`以前列出：  
  
    - `DBPROP_IRowsetUpdate`。  
  
    - `DBPROP_OWNINSERT`： 必须为 READ_ONLY 和为 VARIANT_TRUE。  
  
    - `DBPROP_OWNUPDATEDELETE`： 必须为 READ_ONLY 和为 VARIANT_TRUE。  
  
    - `DBPROP_OTHERINSERT`： 必须为 READ_ONLY 和为 VARIANT_TRUE。  
  
    - `DBPROP_OTHERUPDATEDELETE`： 必须为 READ_ONLY 和为 VARIANT_TRUE。  
  
    - `DBPROP_REMOVEDELETED`： 必须为 READ_ONLY 和为 VARIANT_TRUE。  
  
    - `DBPROP_MAXPENDINGROWS`。  
  
        > [!NOTE]
        >  如果支持通知，您可能还有一些其他属性;请参阅部分`IRowsetNotifyCP`为此列表。  
  
##  <a name="vchowwritingtothedatasource"></a> 写入到数据源  
 若要从数据源中读取，调用`Execute`函数。 若要写入的数据源，请调用`FlushData`函数。 （在常规的意义上，刷新表示以保存对表或索引到磁盘进行的修改。）  

