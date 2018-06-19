---
title: 事务： 在记录集 (ODBC) 执行事务 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- transactions, updating recordsets
ms.assetid: cf1d6b48-7fb8-4903-84f7-a1822054534d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 1d7cae3b05c20736a2e271b574569bcac4d5cdc7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33094600"
---
# <a name="transaction-performing-a-transaction-in-a-recordset-odbc"></a>事务：在记录集中执行事务 (ODBC)
本主题介绍了如何在记录集中执行事务。  
  
> [!NOTE]
>  仅支持一个级别的事务是;你无法嵌套事务。  
  
#### <a name="to-perform-a-transaction-in-a-recordset"></a>在记录集中执行事务  
  
1.  调用`CDatabase`对象的**BeginTrans**成员函数。  
  
2.  如果你不具有实现批量行提取，调用**AddNew/更新**，**编辑/更新**，和**删除**的相同的一个或多个记录集对象的成员函数根据需要多次的数据库。 有关详细信息，请参阅[记录集： 添加、 更新和删除记录 (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)。 如果已实现批量行提取，则必须编写您自己的函数，更新数据源。  
  
3.  最后，调用`CDatabase`对象的**CommitTrans**成员函数。 如果错误发生的一个更新中，或你决定取消所做的更改，调用其**回滚**成员函数。  
  
 下面的示例使用两个记录集从学校注册数据库，将该学生从在其中注册学生的所有类删除学生的注册。 因为**删除**调用这两个记录集内的必须成功，则需要使用事务。 该示例假定存在`m_dbStudentReg`，类型的成员变量`CDatabase`已连接到数据源和记录集类`CEnrollmentSet`和`CStudentSet`。 `strStudentID`变量包含从用户获取的值。  
  
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
>  调用**BeginTrans**试情况下调用**CommitTrans**或**回滚**时出错。  
  
## <a name="see-also"></a>请参阅  
 [事务 (ODBC)](../../data/odbc/transaction-odbc.md)   
 [事务： 事务如何影响更新 (ODBC)](../../data/odbc/transaction-how-transactions-affect-updates-odbc.md)   
 [CDatabase 类](../../mfc/reference/cdatabase-class.md)   
 [CRecordset 类](../../mfc/reference/crecordset-class.md)