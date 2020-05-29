---
title: 事务：在记录集中执行事务 (ODBC)
ms.date: 11/04/2016
helpviewer_keywords:
- transactions, updating recordsets
ms.assetid: cf1d6b48-7fb8-4903-84f7-a1822054534d
ms.openlocfilehash: 45ae414c318376b2c4d787498e9a288a0037af83
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358099"
---
# <a name="transaction-performing-a-transaction-in-a-recordset-odbc"></a>事务：在记录集中执行事务 (ODBC)

本主题介绍如何在记录集中执行事务。

> [!NOTE]
> 仅支持一个级别的事务;不能嵌套事务。

#### <a name="to-perform-a-transaction-in-a-recordset"></a>在记录集中执行事务

1. 调用`CDatabase`对象`BeginTrans`的成员函数。

1. 如果尚未实现批量行提取，请根据需要多次调用同`AddNew/Update`一`Edit/Update`数据库的`Delete`一个或多个记录集对象的 的 和 的成员函数。 有关详细信息，请参阅[记录集：添加、更新和删除记录 （ODBC）。](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md) 如果已实现批量行提取，则必须编写自己的函数来更新数据源。

1. 最后，`CDatabase`调用对象`CommitTrans`的成员函数。 如果其中一个更新中出现错误，或者您决定取消更改，请调用其成员`Rollback`函数。

下面的示例使用两个记录集从学校注册数据库中删除学生的注册，从注册学生的所有班级中删除该学生。 由于两`Delete`个记录集中的调用必须成功，因此需要事务。 该示例假定 存在`m_dbStudentReg`，类型的成员`CDatabase`变量已连接到数据源，以及记录集类`CEnrollmentSet`和`CStudentSet`。 该`strStudentID`变量包含从用户获取的值。

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
> 再次`BeginTrans`调用而不调用`CommitTrans`或`Rollback`是一个错误。

## <a name="see-also"></a>另请参阅

[事务 (ODBC)](../../data/odbc/transaction-odbc.md)<br/>
[事务：事务如何影响更新 (ODBC)](../../data/odbc/transaction-how-transactions-affect-updates-odbc.md)<br/>
[CDatabase 类](../../mfc/reference/cdatabase-class.md)<br/>
[CRecordset 类](../../mfc/reference/crecordset-class.md)
