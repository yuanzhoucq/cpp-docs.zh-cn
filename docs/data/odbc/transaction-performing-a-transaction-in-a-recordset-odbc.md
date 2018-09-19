---
title: 事务： 在记录集 (ODBC) 执行事务 |Microsoft Docs
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
ms.openlocfilehash: 5d73b7c45223c029451f300e495915eb15b0a956
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46103916"
---
# <a name="transaction-performing-a-transaction-in-a-recordset-odbc"></a>事务：在记录集中执行事务 (ODBC)

本主题说明如何在记录集中执行事务。  
  
> [!NOTE]
>  仅支持一个级别的事务是;不能嵌套事务。  
  
#### <a name="to-perform-a-transaction-in-a-recordset"></a>若要在记录集中执行事务  
  
1. 调用`CDatabase`对象的`BeginTrans`成员函数。  
  
1. 如果你尚未实现批量行提取，调用`AddNew/Update`， `Edit/Update`，和`Delete`的很多时候根据需要与相同的数据库的一个或多个记录集对象的成员函数。 有关详细信息，请参阅[记录集： 添加、 更新和删除记录 (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)。 如果已实现批量行提取，则必须编写您自己的函数来更新数据源。  
  
1. 最后，调用`CDatabase`对象的`CommitTrans`成员函数。 如果在更新之一中出现错误，或者你决定取消所做的更改，则调用其`Rollback`成员函数。  
  
下面的示例使用两个记录集从 school 注册数据库，将从学生已注册的所有课程的学生删除学生的注册。 因为`Delete`中这两个记录集的调用必须成功，则需要使用事务。 该示例假定存在`m_dbStudentReg`，类型的成员变量`CDatabase`已连接到数据源和记录集类`CEnrollmentSet`和`CStudentSet`。 `strStudentID`变量包含从用户获取一个值。  
  
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
>  调用`BeginTrans`而无需调用再次`CommitTrans`或`Rollback`是错误。  
  
## <a name="see-also"></a>请参阅  

[事务 (ODBC)](../../data/odbc/transaction-odbc.md)<br/>
[事务：事务如何影响更新 (ODBC)](../../data/odbc/transaction-how-transactions-affect-updates-odbc.md)<br/>
[CDatabase 类](../../mfc/reference/cdatabase-class.md)<br/>
[CRecordset 类](../../mfc/reference/crecordset-class.md)