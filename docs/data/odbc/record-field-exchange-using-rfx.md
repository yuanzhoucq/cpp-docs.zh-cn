---
title: "记录字段交换： 使用 RFX |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- RFX (ODBC), implementing
ms.assetid: ada8f043-37e6-4d41-9db3-92c997a61957
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 28f1cd743a7ede904c99590e56f08b7020f77d82
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="record-field-exchange-using-rfx"></a>记录字段交换：使用 RFX
本主题介绍你如何使用 RFX 相对于框架所执行的操作。  
  
> [!NOTE]
>  本主题适用于从派生的类[CRecordset](../../mfc/reference/crecordset-class.md)中哪些批量行提取尚未实现。 如果你将批量行提取，实现批量记录字段交换 (Bulk RFX)。 批量 RFX 等同于 RFX。 若要了解的差别，请参阅[记录集： 批量获取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
 以下主题包含相关的信息：  
  
-   [记录字段交换： 处理向导代码](../../data/odbc/record-field-exchange-working-with-the-wizard-code.md)介绍 RFX 的主要组件，并说明代码的 MFC 应用程序向导和**添加类**(中所述[添加 MFC ODBC 使用者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)) 为支持 RFX 和如何你可能想要修改向导代码编写。  
  
-   [记录字段交换： 使用 RFX 函数](../../data/odbc/record-field-exchange-using-the-rfx-functions.md)说明中的 RFX 函数编写调用你`DoFieldExchange`重写。  
  
 下表显示你的角色相对于框架为你的用途。  
  
### <a name="using-rfx-you-and-the-framework"></a>使用 RFX： 您和框架  
  
|你|框架|  
|---------|-------------------|  

|声明具有向导记录集类。 指定的字段数据成员的名称和数据类型。 |向导派生`CRecordset`类和写入[DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)为你重写时，请包括 RFX 函数为每个字段数据成员的调用。 |  
|（可选）手动将任何所需的参数数据成员添加到类。 手动添加到的 RFX 函数调用`DoFieldExchange`每个参数数据成员，添加对的调用[CFieldExchange::SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype)组的参数，并指定参数中的总数目[m_nParams](../../mfc/reference/crecordset-class.md#m_nparams). 请参阅[记录集： 参数化记录集 (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)。 | |  
|（可选）手动将附加列绑定到字段数据成员。 手动递增[m_nFields](../../mfc/reference/crecordset-class.md#m_nfields)。 请参阅[记录集： 动态绑定数据列 (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)。 | |  

|构造记录集类的对象。 在之前使用的对象，设置其参数的值数据成员，如果有的话。 |为提高效率，框架预绑定参数，使用 ODBC。 当传递参数值时，框架会将它们传递到数据源。 只使用参数的值发送用于再次查询，除非已更改的排序和/或筛选器字符串。 |  
|打开记录集对象使用[CRecordset::Open](../../mfc/reference/crecordset-class.md#open)。 |执行记录集的查询时，将列绑定到记录集，并在结尾调用字段数据成员`DoFieldExchange`交换的第一个的所选的记录和记录集的字段数据成员之间的数据。 |  
|在记录集中使用的滚动[CRecordset::Move](../../mfc/reference/crecordset-class.md#move)或菜单或工具栏命令。 |调用`DoFieldExchange`将数据传输到的字段数据成员，从新的当前记录。 |  
|添加、 更新和删除记录。 |调用`DoFieldExchange`将数据传输到数据源。 |  
  
## <a name="see-also"></a>请参阅  
 [记录字段交换 (RFX)](../../data/odbc/record-field-exchange-rfx.md)   
 [记录字段交换： RFX 的工作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)   
 [记录集： 获取 Sum 及其他聚合结果 (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)   
 [CRecordset 类](../../mfc/reference/crecordset-class.md)   
 [CFieldExchange 类](../../mfc/reference/cfieldexchange-class.md)   
 [宏、 全局函数和全局变量](../../mfc/reference/mfc-macros-and-globals.md)

