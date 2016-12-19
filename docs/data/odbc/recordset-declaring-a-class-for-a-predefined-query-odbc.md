---
title: "记录集：为预定义查询声明一个类 (ODBC) | Microsoft Docs"
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
  - "ODBC 记录集, 查询"
  - "预定义的查询和记录集"
  - "记录集, 预定义的查询"
  - "记录集, 存储过程"
  - "存储过程, 和记录集"
ms.assetid: d27c4df9-dad2-4484-ba72-92ab0c8ff928
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 记录集：为预定义查询声明一个类 (ODBC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本主题适用于 MFC ODBC 类。  
  
 本主题说明如何创建预定义查询（有时称为“存储过程”，如在 Microsoft SQL Server 中）的记录集类。  
  
> [!NOTE]
>  本主题适用于从 `CRecordset` 派生的对象，这些对象中尚未实现批量取行。  如果已实现批量取行，则进程非常相似。  若要了解实现批量取行的记录集和不实现批量取行的记录集之间的差别，请参见 [记录集：批量获取记录 \(ODBC\)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
 一些数据库管理系统 \(DBMS\) 允许您创建预定义查询并像调用函数那样从程序中调用它。  您创建的查询具有名称，可以接受参数并可以返回记录。  本主题中的过程说明如何调用返回记录（也可能接受参数）的预定义查询。  
  
 数据库类不支持更新预定义查询。  快照预定义查询和动态集预定义查询之间的差别不在于可更新能力，而在于由其他用户（或程序中的其他记录集）所做的更改在您的记录集中是否可见。  
  
> [!TIP]
>  调用不返回记录的预定义查询不需要记录集。  按下面的描述准备 SQL 语句，但要通过调用 `CDatabase` 成员函数 [ExecuteSQL](../Topic/CDatabase::ExecuteSQL.md) 来执行该语句。  
  
 可以创建单个记录集类来管理调用预定义查询，但您必须亲自做一些工作。  向导不支持专为此目的创建类。  
  
#### 创建调用预定义查询（存储过程）的类  
  
1.  使用“添加类”中的 [MFC ODBC 使用者向导](../../mfc/reference/adding-an-mfc-odbc-consumer.md)为提供查询返回的大部分列的表创建记录集类。  这为您提供了一个良好的开端。  
  
2.  为查询返回的、但向导没有创建的任何表中的任何列手动添加字段数据成员。  
  
     例如，如果查询返回三列（每列来自两个其他的表），则向类添加六个（适当数据类型的）字段数据成员。  
  
3.  在类的 [DoFieldExchange](../Topic/CRecordset::DoFieldExchange.md) 成员函数中手动添加 [RFX](../../data/odbc/record-field-exchange-rfx.md) 函数调用，每个 RFX 成员函数对应于每个添加的字段数据成员的数据类型。  
  
    ```  
    Immediately before these RFX calls, call <MSHelp:link keywords="_mfc_CFieldExchange.3a3a.SetFieldType" TABINDEX="0">SetFieldType</MSHelp:link>, as shown here:   
    pFX->SetFieldType( CFieldExchange::outputColumn );  
    ```  
  
    > [!NOTE]
    >  必须知道数据类型和结果集中返回的列顺序。  `DoFieldExchange` 中 RFX 函数调用的顺序必须与结果集中列的顺序相匹配。  
  
4.  为记录集类构造函数中的新字段数据成员手动添加初始化。  
  
     还必须增加 [m\_nFields](../Topic/CRecordset::m_nFields.md) 数据成员的初始化值。  向导编写初始化，但只包括它为您添加的字段数据成员。  例如：  
  
    ```  
    m_nFields += 6;  
    ```  
  
     一些数据类型不应在此初始化，如 `CLongBinary` 或字节数组。  
  
5.  如果查询采用参数，则为每个参数添加参数数据成员、RFX 函数调用和初始化。  
  
6.  必须增加每个已添加参数的 `m_nParams`，就像在上面的步骤 4 中增加已添加字段的 `m_nFields` 那样。  有关更多信息，请参见[记录集：参数化记录集 \(ODBC\)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)。  
  
7.  用下列格式手动编写 SQL 语句字符串：  
  
    ```  
    {CALL proc-name [(? [, ?]...)]}  
    ```  
  
     其中 **CALL** 是一个 ODBC 关键字，**proc\-name** 是查询在数据源中已知的名称，而“?”项是运行时您提供给记录集的参数值的占位符（如果存在）。  下面的示例准备一个参数的占位符：  
  
    ```  
    CString mySQL = "{CALL Delinquent_Accts (?)}";  
    ```  
  
8.  在打开记录集的代码中，首先设置记录集的参数数据成员的值，然后调用 **Open** 成员函数以传递 **lpszSQL** 参数的 SQL 字符串。  或者，替换由类中的 `GetDefaultSQL` 成员函数返回的字符串。  
  
 下面的示例显示调用一个名为 `Delinquent_Accts` 的预定义查询的过程，此查询接受一个销售区域号参数。  此查询返回三列：`Acct_No`、`L_Name` 和 `Phone`。  所有列都来自 Customer 表。  
  
 下面的记录集指定了查询返回的列的字段数据成员和运行时请求的销售区域号参数。  
  
```  
class CDelinquents : public CRecordset  
{  
// Field/Param Data  
    LONG m_lAcct_No;  
    CString m_strL_Name;  
    CString m_strPhone;  
    LONG m_lDistParam;  
    // ...  
};  
```  
  
 除手动添加的 `m_lDistParam` 成员之外，此类声明和向导编写时的一样。  其他成员不在此处显示。  
  
 下一个示例显示 `CDelinquents` 构造函数中数据成员的初始化。  
  
```  
CDelinquents::CDelinquents(CDatabase* pdb)  
   : CRecordset(pdb)  
{  
    // Wizard-generated params:  
    m_lAcct_No = 0;  
    m_strL_Name = "";  
    m_strPhone = "";  
    m_nFields = 3;  
    // User-defined params:  
    m_nParams = 1;  
    m_lDistParam = 0;  
}  
```  
  
 注意 [m\_nFields](../Topic/CRecordset::m_nFields.md) 和 [m\_nParams](../Topic/CRecordset::m_nParams.md) 的初始化。  向导初始化 `m_nFields`；而您初始化 `m_nParams`。  
  
 下一个示例显示 `CDelinquents::DoFieldExchange` 中的 RFX 函数：  
  
```  
void CDelinquents::DoFieldExchange(CFieldExchange* pFX)  
{  
    pFX->SetFieldType(CFieldExchange::outputColumn);  
    RFX_Long(pFX, "Acct_No", m_lAcct_No);  
    RFX_Text(pFX, "L_Name", m_strL_Name);  
    RFX_Text(pFX, "Phone", m_strPhone);  
    pFX->SetFieldType(CFieldExchange::param);  
    RFX_Long(pFX, "Dist_No", m_lDistParam);  
}  
```  
  
 除了生成三个返回列的 RFX 调用，此代码还管理绑定您在运行时传递的参数。  参数被设为 `Dist_No`（区域号）列的关键字。  
  
 下一个示例显示如何设置 SQL 字符串和如何使用 SQL 字符串打开记录集。  
  
```  
// Construct a CDelinquents recordset object  
CDelinquents rsDel( NULL );  
CString strSQL = "{CALL Delinquent_Accts (?)}"  
// Specify a parameter value (obtained earlier from the user)  
rsDel.m_lDistParam = lDistrict;  
// Open the recordset and run the query  
if( rsDel.Open( CRecordset::snapshot, strSQL ) )  
    // Use the recordset ...  
```  
  
 此代码构造快照、给快照传递以前从用户获得的参数并调用预定义查询。  查询运行时，它返回指定销售区域的记录。  每个记录都包含帐号、客户的姓氏以及客户的电话号码等列。  
  
> [!TIP]
>  可能需要处理来自存储过程的返回值（输出参数）。  有关更多信息和示例，请参见 [CFieldExchange::SetFieldType](../Topic/CFieldExchange::SetFieldType.md)。  
  
## 请参阅  
 [记录集 \(ODBC\)](../../data/odbc/recordset-odbc.md)   
 [记录集：再次查询记录集 \(ODBC\)](../../data/odbc/recordset-requerying-a-recordset-odbc.md)   
 [记录集：声明表的类 \(ODBC\)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)   
 [记录集：执行联接 \(ODBC\)](../../data/odbc/recordset-performing-a-join-odbc.md)