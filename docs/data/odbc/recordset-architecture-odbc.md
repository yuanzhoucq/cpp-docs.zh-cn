---
title: "记录集：体系结构 (ODBC) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "字段数据成员"
  - "字段数据成员, 记录集体系结构"
  - "m_nFields 数据成员"
  - "m_nFields 数据成员, 记录集"
  - "m_nParams 数据成员"
  - "m_nParams 数据成员, 记录集"
  - "ODBC 记录集, 体系结构"
  - "记录集内的参数数据成员"
  - "记录集, 体系结构"
  - "记录集, 数据成员"
ms.assetid: 47555ddb-11be-4b9e-9b9a-f2931764d298
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 记录集：体系结构 (ODBC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本主题适用于 MFC ODBC 类。  
  
 本文描述构成记录集对象结构的数据成员：  
  
-   [字段数据成员](#_core_field_data_members)  
  
-   [参数数据成员](#_core_parameter_data_members)  
  
-   [使用 m\_nFields 和 m\_nParams 数据成员](#_core_using_m_nfields_and_m_nparams)  
  
> [!NOTE]
>  本主题适用于从 `CRecordset` 派生的对象，这些对象中尚未实现批量取行。  如果已实现批量取行，则结构与此相似。  若要了解其中的差别，请参见[记录集：批量获取记录 \(ODBC\)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
##  <a name="_core_a_sample_class"></a> 示例类  
 当使用“添加类”向导中的 [MFC ODBC 使用者向导](../../mfc/reference/adding-an-mfc-odbc-consumer.md)声明从 `CRecordset` 派生的记录集类时，产生的类具有下列示例类所显示的通用结构：  
  
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
  
 在类的开头，该向导写一组[字段数据成员](#_core_field_data_members)。  创建此类时，必须指定一个或多个字段数据成员。  如果此类和示例类（带有数据成员 `m_strIDParam`）一样被参数化，则必须手动添加[参数数据成员](#_core_parameter_data_members)。  该向导不支持向类添加参数。  
  
##  <a name="_core_field_data_members"></a> 字段数据成员  
 记录集类中最重要的成员是字段数据成员。  对于从数据源中选择的每一列，此类包含具有适合该列的数据类型的数据成员。  例如，本文开头显示的[示例类](#_core_a_sample_class)有两个字段数据成员，两者都为 `CString` 类型，名称为 `m_strCourseID` 和 `m_strCourseTitle`。  
  
 当记录集选择一组记录时，框架会自动将当前记录（在 **Open** 调用后，第一条记录即为当前记录）的列绑定到对象的字段数据成员上。  也就是说，框架将合适的字段数据成员用作缓冲区，在该缓冲区中存储记录列的内容。  
  
 当用户滚动到一条新记录时，框架使用字段数据成员表示当前记录。  框架通过替换以前记录的值来刷新字段数据成员。  字段数据成员还用于更新当前记录以及添加新记录。  作为记录更新进程的一部分，通过直接给一个或多个适当的字段数据成员赋值来指定更新值。  
  
##  <a name="_core_parameter_data_members"></a> 参数数据成员  
 若类被参数化，它将有一个或多个参数数据成员。  参数化类使您可以根据运行时获取或计算的信息创建记录集查询。  
  
 通常，参数可帮助缩小选项范围，如下面的示例所示。  基于本文开头的[示例类](#_core_a_sample_class)，记录集对象可能执行以下 SQL 语句：  
  
```  
SELECT CourseID, CourseTitle FROM Course WHERE CourseID = ?  
```  
  
 “?”是在运行时提供的参数值的占位符。  当构造记录集并将其 `m_strIDParam` 数据成员设置为“MATH101”时，记录集的有效 SQL 语句变成：  
  
```  
SELECT CourseID, CourseTitle FROM Course WHERE CourseID = MATH101  
```  
  
 通过定义参数数据成员，将 SQL 字符串中的参数通知框架。  框架绑定参数，该参数使 ODBC 可以知道从何处获得用于替换占位符的值。  在该示例中，结果记录集只包含 Course 表中 CourseID 列的值为“MATH101”的记录。  该记录中的所有指定列都被选定。  可以根据需要指定多个参数（和占位符）。  
  
> [!NOTE]
>  MFC 本身并不操作参数，尤其不执行文本替换。  相反，MFC 通知 ODBC 在何处获得参数；ODBC 检索数据并执行必要的参数化操作。  
  
> [!NOTE]
>  参数的顺序很重要。  有关参数及参数顺序的更多信息，请参见[记录集：参数化记录集 \(ODBC\)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)。  
  
##  <a name="_core_using_m_nfields_and_m_nparams"></a> 使用 m\_nFields 和 m\_nParams  
 向导在编写类的构造函数时，还初始化 [m\_nFields](../Topic/CRecordset::m_nFields.md) 数据成员，该数据成员指定类中的[字段数据成员](#_core_field_data_members)数目。  如果向类添加任何[参数](#_core_parameter_data_members)，则还必须添加 [m\_nParams](../Topic/CRecordset::m_nParams.md) 数据成员的初始化，以指定参数数据成员的数目。  框架使用这些值来处理数据成员。  
  
 有关更多信息和示例，请参见[记录字段交换：使用 RFX](../../data/odbc/record-field-exchange-using-rfx.md)。  
  
## 请参阅  
 [记录集 \(ODBC\)](../../data/odbc/recordset-odbc.md)   
 [记录集：声明表的类 \(ODBC\)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)   
 [记录字段交换 \(RFX\)](../../data/odbc/record-field-exchange-rfx.md)