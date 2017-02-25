---
title: "事务：在记录集中执行事务 (ODBC) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "事务, 更新记录集"
ms.assetid: cf1d6b48-7fb8-4903-84f7-a1822054534d
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# 事务：在记录集中执行事务 (ODBC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本主题说明如何在记录集中执行事务。  
  
> [!NOTE]
>  只支持一个事务级别，不能嵌套事务。  
  
#### 在记录集中执行事务  
  
1.  调用 `CDatabase` 对象的 **BeginTrans** 成员函数。  
  
2.  如果尚未实现批量取行，可多次调用同一数据库一个或多个记录集对象的 **AddNew\/Update**、**Edit\/Update** 和 **Delete** 成员函数。  有关更多信息，请参见 [记录集：添加、更新和删除记录 \(ODBC\)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)。  如果已实现批量取行，则必须写自己的函数来更新数据源。  
  
3.  最后，调用 `CDatabase` 对象的 **CommitTrans** 成员函数。  如果其中的一个更新中出现错误，或者决定取消更改，请调用 **Rollback** 成员函数。  
  
 下面的示例使用两个记录集从学校注册数据库中删除一个学生的登记，将该学生从所登记的所有课程中删除。  由于两个记录集中的 **Delete** 调用都必须成功，因此需要一个事务。  该示例假定存在 `m_dbStudentReg`、一个已连接到数据源的 `CDatabase` 类型的成员变量以及记录集类 `CEnrollmentSet` 和 `CStudentSet`。  `strStudentID` 变量包含从用户获得的一个值。  
  
```  
BOOL CEnrollDoc::RemoveStudent( CString strStudentID )  
{  
    // remove student from all the classes  
    // the student is enrolled in  
  
    if ( !m_dbStudentReg.BeginTrans( ) )  
        return FALSE;  
  
    CEnrollmentSet rsEnrollmentSet(&m_dbStudentReg);  
    rsEnrollmentSet.m_strFilter = "StudentID = " + strStudentID;  
  
    if ( !rsEnrollmentSet.Open(CRecordset::dynaset) )  
        return FALSE;  
  
    CStudentSet rsStudentSet(&m_dbStudentReg);  
    rsStudentSet.m_strFilter = "StudentID = " + strStudentID;  
  
    if ( !rsStudentSet.Open(CRecordset::dynaset) )  
        return FALSE;  
  
    TRY  
    {  
        while ( !rsEnrollmentSet.IsEOF( ) )  
        {  
            rsEnrollmentSet.Delete( );  
            rsEnrollmentSet.MoveNext( );  
        }  
  
        // delete the student record  
        rsStudentSet.Delete( );  
  
        m_dbStudentReg.CommitTrans( );  
    }  
  
    CATCH_ALL(e)  
    {  
        m_dbStudentReg.Rollback( );  
        return FALSE;  
    }  
    END_CATCH_ALL  
  
    rsEnrollmentSet.Close( );  
    rsStudentSet.Close( );  
  
    return TRUE;  
  
}  
```  
  
> [!NOTE]
>  未经调用 **CommitTrans** 或 **Rollback** 就再次调用 **BeginTrans** 是错误的。  
  
## 请参阅  
 [事务 \(ODBC\)](../../data/odbc/transaction-odbc.md)   
 [事务：事务如何影响更新 \(ODBC\)](../../data/odbc/transaction-how-transactions-affect-updates-odbc.md)   
 [CDatabase Class](../../mfc/reference/cdatabase-class.md)   
 [CRecordset Class](../../mfc/reference/crecordset-class.md)