---
title: "填充列表框从第二个记录集 （MFC 数据访问） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- record views, filling list boxes
- list boxes, filling from second recordset
- recordsets [C++], filling list boxes or combo boxes
- CComboBox class, filling object from second rowset
- ODBC recordsets [C++], filling list boxes or combo boxes
- combo boxes [C++], filling from second recordset
- CListCtrl class, filling from second recordset
ms.assetid: 360c0834-da6b-4dc0-bcea-80e9acd611f0
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 6e411ebcf40099a2236048dd8f151b438fe5b947
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="filling-a-list-box-from-a-second-recordset--mfc-data-access"></a>从另一个记录集填充列表框（MFC 数据访问）
默认情况下，记录视图与其字段映射到记录视图控件的单个记录集对象有关。 有时，你可能需要在记录视图中放置列表框或组合框控件，并使用来自另一个记录集对象的值填充。 用户可以使用列表框选择要在记录视图中显示的新类别信息。 本主题将介绍此操作的方法和时间。  
  
> [!TIP]
>  请注意，从数据源填充组合框或列表框速度可能比较慢。 请采取措施，防止试图从具有大量记录的记录集填充控件。  
  
 本主题的模型由填充窗体控件的主要记录集组成，而辅助记录集则填充列表框或组合框。 选择列表框中的字符串将导致你的程序根据所选的类型重新查询主要记录集。 以下过程使用的是组合框，但同样也适用于列表框。  
  
#### <a name="to-fill-a-combo-box-or-list-box-from-a-second-recordset"></a>要从另一个记录集填充组合框或列表框  
  
1.  创建记录集对象 ([CRecordset](../mfc/reference/crecordset-class.md)。  
  
2.  获取指向的[CComboBox](../mfc/reference/ccombobox-class.md)组合框控件的对象。  
  
3.  清空组合框以前的所有内容。  
  
4.  浏览记录集中的所有记录调用[ccombobox::](../mfc/reference/ccombobox-class.md#addstring)从你想要添加到组合框的当前记录每个字符串。  
  
5.  初始化组合框中的选择。  
  
```  
void CSectionForm::OnInitialUpdate()  
{  
    // ...  
  
    // Fill the combo box with all of the courses  
    CENROLLDoc* pDoc = GetDocument();  
    if (!pDoc->m_courseSet.Open())  
        return;  
  
    // ...  
  
    m_ctlCourseList.ResetContent();  
    if (pDoc->m_courseSet.IsOpen())  
    {   
        while (!pDoc->m_courseSet.IsEOF() )  
        {  
            m_ctlCourseList.AddString(  
                pDoc->m_courseSet.m_CourseID);  
            pDoc->m_courseSet.MoveNext();  
        }  
    }  
    m_ctlCourseList.SetCurSel(0);  
}  
```  
  
 此函数使用另一个记录集 `m_courseSet`，该记录集含有所提供的所有课程的记录和一个存储在记录视图类中的 `CComboBox` 控件 `m_ctlCourseList`。  
  
 此函数可从文档获取 `m_courseSet` 并将其打开。 然后清空 `m_ctlCourseList` 并浏览 `m_courseSet`。 对于每一条记录，函数都会调用组合框的 `AddString` 成员函数来添加记录的课程 ID 值。 最后，代码设置组合框选择。  
  
## <a name="see-also"></a>请参阅  
 [记录视图 （MFC 数据访问）](../data/record-views-mfc-data-access.md)   
 [ODBC 驱动程序列表](../data/odbc/odbc-driver-list.md)