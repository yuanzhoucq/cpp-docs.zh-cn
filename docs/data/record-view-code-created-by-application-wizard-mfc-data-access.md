---
title: 记录视图代码创建的应用程序向导 （MFC 数据访问） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- application wizards [C++], record view code
- record views, refreshing controls
- record views, application wizard code
ms.assetid: 18fd4703-5939-491d-b759-985f767b951f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 15355d156b3c85c8f99ba638b30f831da96686af
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="record-view-code-created-by-application-wizard--mfc-data-access"></a>应用程序向导创建的记录视图代码（MFC 数据访问）
[MFC 应用程序向导](../mfc/reference/database-support-mfc-application-wizard.md)替代视图的`OnInitialUpdate`和`OnGetRecordset`成员函数。 在框架创建框架窗口、文档和视图之后，将调用 `OnInitialUpdate` 以便初始化视图。 `OnInitialUpdate` 从文档获取指向记录集的指针。 对基类的调用[cview:: Oninitialupdate](../mfc/reference/cview-class.md#oninitialupdate)函数打开记录集。 下面的代码演示此流程的`CRecordView`:  
  
```  
void CSectionForm::OnInitialUpdate()  
{  
   m_pSet = &GetDocument()->m_sectionSet;  
   CRecordView::OnInitialUpdate();  
}  
```  
  
 记录集打开时会选择记录。 [CRecordset::Open](../mfc/reference/crecordset-class.md#open)使第一条记录的当前记录和 DDX 移动数据的记录集的字段数据成员到相应的表单控件的视图中。 有关 RFX 的详细信息，请参阅[记录字段交换 (RFX)](../data/odbc/record-field-exchange-rfx.md)。 有关 DDX 的详细信息，请参阅[对话框数据交换和验证](../mfc/dialog-data-exchange-and-validation.md)。 有关文档/视图创建过程的信息，请参阅[使用类编写 Windows 应用程序到](../mfc/using-the-classes-to-write-applications-for-windows.md)。  
  
> [!NOTE]
>  你应使你的最终用户有能力刷新记录集的记录视图控件。 若没有此能力，当用户将控件的值更改为非法值时，用户可能会永远停滞在当前的记录。 若要刷新控件，请调用`CWnd`成员函数[UpdateData](../mfc/reference/cwnd-class.md#updatedata)其中参数**FALSE**。  
  
## <a name="see-also"></a>请参阅  
 [使用记录视图](../data/using-a-record-view-mfc-data-access.md)