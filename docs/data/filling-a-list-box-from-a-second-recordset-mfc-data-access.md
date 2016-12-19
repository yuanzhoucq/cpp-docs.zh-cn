---
title: "从另一个记录集填充列表框（MFC 数据访问） | Microsoft Docs"
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
  - "CComboBox 类, 从第二个行集合填充对象"
  - "CListCtrl 类, 从第二个记录集填充"
  - "组合框 [C++], 从第二个记录集填充"
  - "DAO 记录集"
  - "DAO 记录集, 填充列表框或组合框"
  - "填充列表或组合框"
  - "列表框, 从第二个记录集填充"
  - "记录视图中的多记录集"
  - "ODBC 记录集 [C++], 填充列表框或组合框"
  - "记录视图, 填充列表框"
  - "记录集 [C++], 填充列表框或组合框"
ms.assetid: 360c0834-da6b-4dc0-bcea-80e9acd611f0
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 从另一个记录集填充列表框（MFC 数据访问）
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

默认情况下，记录视图与其字段映射到记录视图控件的单个记录集对象有关。  有时，你可能需要在记录视图中放置列表框或组合框控件，并使用来自另一个记录集对象的值填充。  用户可以使用列表框选择要在记录视图中显示的新类别信息。  本主题将介绍此操作的方法和时间。  
  
> [!TIP]
>  请注意，从数据源填充组合框或列表框速度可能比较慢。  请采取措施，防止试图从具有大量记录的记录集填充控件。  
  
 本主题的模型由填充窗体控件的主要记录集组成，而辅助记录集则填充列表框或组合框。  选择列表框中的字符串将导致你的程序根据所选的类型重新查询主要记录集。  以下过程使用的是组合框，但同样也适用于列表框。  
  
#### 要从另一个记录集填充组合框或列表框  
  
1.  创建记录集对象 \(用于 ODBC 的 [CRecordset](../mfc/reference/crecordset-class.md)和用于 DAO 的 [CDaoRecordset](../mfc/reference/cdaorecordset-class.md)）。  
  
2.  获取组合框控件的 [CComboBox](../mfc/reference/ccombobox-class.md) 对象的指针。  
  
3.  清空组合框以前的所有内容。  
  
4.  浏览记录集中的所有记录，从你想要添加到组合框的当前记录调用每个字符串的 [CComboBox::AddString](../Topic/CComboBox::AddString.md)。  
  
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
  
 此函数可从文档获取 `m_courseSet` 并将其打开。  然后清空 `m_ctlCourseList` 并浏览 `m_courseSet`。  对于每一条记录，函数都会调用组合框的 `AddString` 成员函数来添加记录的课程 ID 值。  最后，代码设置组合框选择。  
  
## 请参阅  
 [记录视图（MFC 数据访问）](../data/record-views-mfc-data-access.md)   
 [ODBC 驱动程序列表](../data/odbc/odbc-driver-list.md)