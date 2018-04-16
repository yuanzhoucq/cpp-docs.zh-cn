---
title: "记录字段交换： 使用 RFX 函数 |Microsoft 文档"
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
- ODBC [C++], data types
- data types [C++], ODBC record field exchange
- RFX (ODBC) [C++], function syntax and parameters
- DoFieldExchange method, and RFX functions
- ODBC [C++], RFX
- RFX (ODBC) [C++], data types
- function calls, RFX functions
ms.assetid: c594300b-5a29-4119-a68b-e7ca32def696
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a270b26fc0fd9be721ee0656f9f0d14ab579b477
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="record-field-exchange-using-the-rfx-functions"></a>记录字段交换：使用 RFX 函数
本主题说明如何使用构成的主体 RFX 函数调用你`DoFieldExchange`重写。  
  
> [!NOTE]
>  本主题适用于从派生的类[CRecordset](../../mfc/reference/crecordset-class.md)中哪些批量行提取尚未实现。 如果你将批量行提取，实现批量记录字段交换 (Bulk RFX)。 批量 RFX 等同于 RFX。 若要了解的差别，请参阅[记录集： 批量获取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
 RFX 全局函数交换在记录集中的数据源和字段数据成员上的列之间的数据。 你编写记录集的调用 RFX 函数[DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)成员函数。 本主题简要介绍了函数，并显示对其使用 RFX 函数均可用的数据类型。 [技术说明 43](../../mfc/tn043-rfx-routines.md)介绍如何为其他数据类型编写您自己的 RFX 函数。  
  
##  <a name="_core_rfx_function_syntax"></a>RFX 函数语法  
 每个 RFX 函数采用三个参数 （和有些方法采用一个可选的第四个或第五个参数）：  
  
-   指向的指针[CFieldExchange](../../mfc/reference/cfieldexchange-class.md)对象。 你只需传递`pFX`指针传递给`DoFieldExchange`。  
  
-   它的列名称出现在数据源。  
  
-   记录集类中的参数数据成员的对应字段数据成员的名称。  
  
-   （可选）在某些函数、 字符串或传输的数组的最大长度。 这将默认为 255 个字节，但你可能想要对其进行更改。 最大大小取决于的最大大小`CString`对象- **INT_MAX** (2,147,483,647) 个字节，但你可能会遇到该大小前的驱动程序限制。  
  
-   （可选）在`RFX_Text`函数，你有时使用第五个参数来指定列的数据类型。  
  
 有关详细信息，请参阅下的 RFX 函数[宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)中*类库参考*。 当你可能会使特殊的示例使用的参数，请参阅[记录集： 获取 Sum 及其他聚合结果 (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)。  
  
##  <a name="_core_rfx_data_types"></a>RFX 数据类型  
 类库提供数据源和你的记录集之间传输许多不同的数据类型的 RFX 的函数。 以下列表总结了 RFX 函数按数据类型。 在你必须在其中编写你自己 RFX 函数调用的情况下，选择按数据类型从这些函数。  
  
|函数|数据类型|  
|--------------|---------------|  
|`RFX_Bool`|**BOOL**|  
|`RFX_Byte`|**BYTE**|  
|`RFX_Binary`|`CByteArray`|  
|`RFX_Double`|**double**|  
|`RFX_Single`|**float**|  
|`RFX_Int`|`int`|  
|`RFX_Long`|**long**|  
|`RFX_LongBinary`|`CLongBinary`|  
|`RFX_Text`|`CString`|  
|`RFX_Date`|`CTime`|  
  

 有关详细信息，请参阅 RFX 函数文档下,[宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)中*类库参考*。 有关 c + + 数据类型如何映射到 SQL 数据类型的信息，请参阅 ANSI SQL 数据类型映射到 c + + 数据类型的表中[SQL: SQL 和 c + + 数据类型 (ODBC)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md)。  
  
## <a name="see-also"></a>请参阅  
 [记录字段交换 (RFX)](../../data/odbc/record-field-exchange-rfx.md)   
 [记录字段交换： RFX 的工作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)   
 [记录集： 参数化记录集 (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)   
 [记录集： 动态绑定数据列 (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)   
 [CRecordset 类](../../mfc/reference/crecordset-class.md)   
 [CFieldExchange 类](../../mfc/reference/cfieldexchange-class.md)