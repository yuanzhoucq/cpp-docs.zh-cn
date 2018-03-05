---
title: "记录集： 为预定义的查询 (ODBC) 声明一个类 |Microsoft 文档"
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
- ODBC recordsets, queries
- predefined queries and recordsets
- stored procedures, and recordsets
- recordsets, predefined queries
- recordsets, stored procedures
ms.assetid: d27c4df9-dad2-4484-ba72-92ab0c8ff928
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 8ecdc146610fe20dcc007d6b1223d7108e1ee595
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="recordset-declaring-a-class-for-a-predefined-query-odbc"></a>记录集：为预定义查询声明一个类 (ODBC)
本主题适用于 MFC ODBC 类。  
  
 本主题说明如何创建预定义的查询 （有时称为存储的过程，如 Microsoft SQL Server 中所示） 的记录集类。  
  
> [!NOTE]
>  本主题适用于派生自`CRecordset`中哪些批量行提取尚未实现。 如果已实现批量行提取，此过程是非常类似。 若要了解和一些未实现批量行提取的记录集之间的差别，请参阅[记录集： 批量获取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
 某些数据库管理系统 (Dbms)，可以创建预定义的查询，并从你的程序与函数一样调用它。 查询有一个名称，可能需要参数，并且可能会返回记录。 本主题中的过程描述如何调用预定义的查询返回的记录 （并且可能采用参数）。  
  
 数据库类不支持更新预定义的查询。 快照预定义的查询和动态集预定义的查询之间的差异不 updateability 而由其他用户 （或其他程序中的记录集） 进行的更改是否在记录集中中可见。  
  
> [!TIP]
>  不需要要调用预定义的查询不返回记录的记录集。 准备 SQL 语句，如下所述，但通过调用执行`CDatabase`成员函数[ExecuteSQL](../../mfc/reference/cdatabase-class.md#executesql)。  
  
 你可以创建一个单个记录集类来管理调用预定义的查询，但您必须亲自做一些工作。 向导不支持创建专为此目的的类。  
  
#### <a name="to-create-a-class-for-calling-a-predefined-query-stored-procedure"></a>若要创建一个类用于调用预定义的查询 （存储过程）  
  
1.  使用[MFC ODBC 使用者向导](../../mfc/reference/adding-an-mfc-odbc-consumer.md)从**添加类**创建提供的大部分查询返回的列的表的记录集类。 这将提供一个良好的开端。  
  
2.  手动添加所有属于该查询将返回，但向导未为你创建的任何表的列的字段数据成员。  
  
     例如，如果查询返回从两个其他表的三个列，则可添加到类 （的适当的数据类型中） 的六个字段数据成员。  
  
3.  手动添加[RFX](../../data/odbc/record-field-exchange-rfx.md)函数调用中[DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)类，一个对应于每个数据类型的成员函数添加字段数据成员。  
  
    ```  
    Immediately before these RFX calls, call <MSHelp:link keywords="_mfc_CFieldExchange.3a3a.SetFieldType" TABINDEX="0">SetFieldType</MSHelp:link>, as shown here:   
    pFX->SetFieldType( CFieldExchange::outputColumn );  
    ```  
  
    > [!NOTE]
    >  你必须知道数据类型和设置在结果中返回的列的顺序。 RFX 函数的顺序调用`DoFieldExchange`结果集中的列的顺序必须匹配。  
  
4.  手动添加为新的字段数据成员的初始化过程中，在记录集类构造函数。  
  
     你还必须递增的初始化值[m_nFields](../../mfc/reference/crecordset-class.md#m_nfields)数据成员。 向导会将写入初始化，但它仅涵盖它为您添加的字段数据成员。 例如:  
  
    ```  
    m_nFields += 6;  
    ```  
  
     某些数据类型不应对进行初始化在这里，例如，`CLongBinary`或字节数组。  
  
5.  如果查询采用参数，添加每个参数、 RFX 函数调用和每个初始化的参数数据成员。  
  
6.  必须递增`m_nParams`每个已添加参数，就像`m_nFields`对于此过程的步骤 4 中添加字段。 有关详细信息，请参阅[记录集： 参数化记录集 (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)。  
  
7.  手动编写 SQL 语句字符串具有以下形式：  
  
    ```  
    {CALL proc-name [(? [, ?]...)]}  
    ```  
  
     其中**调用**是 ODBC 关键字时，**进程名称**是查询的名称，因为数据源，知道与"？"项是你提供到记录集在运行时 （如果有） 的参数值的占位符. 下面的示例准备一个参数的占位符：  
  
    ```  
    CString mySQL = "{CALL Delinquent_Accts (?)}";  
    ```  
  
8.  在代码中，打开记录集，设置的记录集的参数的值数据成员，然后调用**打开**成员函数，传递 SQL 字符串**lpszSQL**参数。 相反，将通过返回的字符串或`GetDefaultSQL`类中的成员函数。  
  
 下面的示例演示调用名为的预定义的查询的过程`Delinquent_Accts`，其中的一个销售区域号采用一个参数。 此查询返回三列： `Acct_No`， `L_Name`， `Phone`。 所有列都都来自客户表。  
  
 下面的记录集指定的查询将返回和销售的参数地区在运行时请求数目的列的字段数据成员。  
  
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
  
 此类声明为向导会将它，写入除`m_lDistParam`手动添加的成员。 此处不显示其他成员。  
  
 下面的示例演示中的数据成员的初始化`CDelinquents`构造函数。  
  
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
  
 请注意有关初始化[m_nFields](../../mfc/reference/crecordset-class.md#m_nfields)和[m_nParams](../../mfc/reference/crecordset-class.md#m_nparams)。 向导正在进行初始化`m_nFields`; 您初始化`m_nParams`。  
  
 下面的示例演示中的 RFX 函数`CDelinquents::DoFieldExchange`:  
  
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
  
 除了生成三个返回的列的 RFX 调用，此代码还管理绑定在运行时传递的参数。 参数进行键控到`Dist_No`（区域号） 列。  
  
 下面的示例演示如何设置 SQL 字符串以及如何使用它来打开记录集。  
  
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
  
 此代码构造快照、 将其传递从用户之前获取的参数和调用预定义的查询。 当查询运行时，会将返回指定的销售区域的记录。 每个记录包含列的帐号、 客户的最后一个名称和客户的电话号码。  
  
> [!TIP]
>  你可能想要处理来自存储过程的返回值 （输出参数）。 有关详细信息及示例，请参阅[CFieldExchange::SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype)。  
  
## <a name="see-also"></a>请参阅  
 [记录集 (ODBC)](../../data/odbc/recordset-odbc.md)   
 [记录集： 再次查询记录集 (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md)   
 [记录集： 声明表 (ODBC) 类](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)   
 [记录集：执行联接 (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md)