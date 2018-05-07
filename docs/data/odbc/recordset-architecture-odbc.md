---
title: 记录集： 体系结构 (ODBC) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- recordsets, data members
- field data members, recordset architecture
- field data members
- m_nParams data member, recordsets
- recordsets, architecture
- parameter data members in recordsets
- m_nFields data member
- ODBC recordsets, architecture
- m_nParams data member
- m_nFields data member, recordsets
ms.assetid: 47555ddb-11be-4b9e-9b9a-f2931764d298
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5be3ec16ec01a6c6db2e24b1b6a6260f3a44bfec
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="recordset-architecture-odbc"></a>记录集：体系结构 (ODBC)
本主题适用于 MFC ODBC 类。  
  
 本主题介绍了构成的记录集对象的体系结构的数据成员：  
  
-   [字段数据成员](#_core_field_data_members)  
  
-   [参数数据成员](#_core_parameter_data_members)  
  
-   [使用 m_nFields 和 m_nParams 数据成员](#_core_using_m_nfields_and_m_nparams)  
  
> [!NOTE]
>  本主题适用于派生自`CRecordset`中哪些批量行提取尚未实现。 如果实现批量行提取，体系结构非常相似。 若要了解的差别，请参阅[记录集： 批量获取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
##  <a name="_core_a_sample_class"></a> 示例类  
 当你使用[MFC ODBC 使用者向导](../../mfc/reference/adding-an-mfc-odbc-consumer.md)从**添加类**向导来声明一个记录集的类派生自`CRecordset`，生成的类具有如下所示简单的一般结构类：  
  
```  
class CCourse : public CRecordset  
{  
public:  
   CCourse(CDatabase* pDatabase = NULL);  
   ...  
   CString m_strCourseID;  
   CString m_strCourseTitle;  
   CString m_strIDParam;  
};  
```  
  
 在类的开头，向导会将写入一套[字段数据成员](#_core_field_data_members)。 在创建类时，你必须指定一个或多个字段数据成员。 如果类进行参数化，因为示例类是 (与数据成员`m_strIDParam`)，则必须手动添加[参数数据成员](#_core_parameter_data_members)。 向导不支持向类添加参数。  
  
##  <a name="_core_field_data_members"></a> 字段数据成员  
 记录集类的最重要成员是字段数据成员。 对于从数据源选择每个列，此类包含该列的适当的数据类型的数据成员。 例如，[示例类](#_core_a_sample_class)这开头显示主题包含两个字段数据成员，这两个类型`CString`、 调用`m_strCourseID`和`m_strCourseTitle`。  
  
 当记录集选择一组记录时，框架会自动将当前记录的列 (后**打开**调用，第一条记录是最新) 的对象的字段数据成员。 也就是说，框架将使用相应的字段数据成员作为要在其中存储记录列的内容的缓冲区。  
  
 在用户滚动到一条新记录时，框架会使用的字段数据成员来表示当前记录。 框架刷新字段数据成员，替换上一条记录的值。 字段数据成员也用于更新当前记录和添加新记录。 更新记录的过程的一部分，你可以通过直接向相应的字段数据成员或成员分配的值来指定更新值。  
  
##  <a name="_core_parameter_data_members"></a> 参数数据成员  
 如果类参数化，它具有一个或多个参数数据成员。 参数化的类，可以创建记录集查询的基础获取或在运行时计算的信息。  
  
 通常情况下，参数有助于缩小所选内容，如以下示例所示。 基于[示例类](#_core_a_sample_class)记录集对象可能会在本主题开头，执行以下 SQL 语句：  
  
```  
SELECT CourseID, CourseTitle FROM Course WHERE CourseID = ?  
```  
  
 "？"是在运行时提供的参数值的占位符。 记录集的构造时并设置其`m_strIDParam`MATH101 到的数据成员，记录集的有效 SQL 语句将变为：  
  
```  
SELECT CourseID, CourseTitle FROM Course WHERE CourseID = MATH101  
```  
  
 通过定义的参数数据成员，你告知框架 SQL 字符串中的参数。 框架将绑定的参数，这样就知道从何处获取值替换占位符的 ODBC。 在示例中，生成的记录集包含仅从包含其值是 MATH101 CourseID 列的课程表的记录。 选择该记录的所有指定的列。 你可以指定任意数量的参数 （和占位符） 根据你的需要。  
  
> [!NOTE]
>  MFC 本身并不操作使用的参数-具体而言，它不执行文本替换。 相反，MFC 告知 ODBC 从何处获取参数;ODBC 中检索数据并执行必要的参数化。  
  
> [!NOTE]
>  参数的顺序很重要。 此类信息的和参数的详细信息，请参阅[记录集： 参数化记录集 (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)。  
  
##  <a name="_core_using_m_nfields_and_m_nparams"></a> 使用 m_nFields 和 m_nParams  

 当向导编写你的类的构造函数时，它还会初始化[m_nFields](../../mfc/reference/crecordset-class.md#m_nfields)数据成员，指定的数[字段数据成员](#_core_field_data_members)类中。 如果你将任何添加[参数](#_core_parameter_data_members)到该类，则还必须添加的初始化[m_nParams](../../mfc/reference/crecordset-class.md#m_nparams)数据成员，指定参数数据成员的数目。 框架使用这些值来使用数据成员。  
  
 有关详细信息和示例，请参阅[记录字段交换： 使用 RFX](../../data/odbc/record-field-exchange-using-rfx.md)。  
  
## <a name="see-also"></a>请参阅  
 [记录集 (ODBC)](../../data/odbc/recordset-odbc.md)   
 [记录集： 声明表 (ODBC) 类](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)   
 [记录字段交换 (RFX)](../../data/odbc/record-field-exchange-rfx.md)