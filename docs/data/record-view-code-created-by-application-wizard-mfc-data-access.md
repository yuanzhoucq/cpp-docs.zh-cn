---
title: "应用程序向导创建的记录视图代码（MFC 数据访问） | Microsoft Docs"
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
  - "应用程序向导 [C++], 记录视图代码"
  - "记录视图, 应用程序向导代码"
  - "记录视图, 刷新控件"
ms.assetid: 18fd4703-5939-491d-b759-985f767b951f
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# 应用程序向导创建的记录视图代码（MFC 数据访问）
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[MFC 应用程序向导](../mfc/reference/database-support-mfc-application-wizard.md)将重写视图的 `OnInitialUpdate` 和 `OnGetRecordset` 成员函数。  在框架创建框架窗口、文档和视图之后，将调用 `OnInitialUpdate` 以便初始化视图。  `OnInitialUpdate` 从文档获取指向记录集的指针。  调用基类 [CView::OnInitialUpdate](../Topic/CView::OnInitialUpdate.md) 函数打开记录集。  以下代码显示了 `CRecordView` 的过程 — `CDaoRecordView` 的代码类似：  
  
```  
void CSectionForm::OnInitialUpdate()  
{  
   m_pSet = &GetDocument()->m_sectionSet;  
   CRecordView::OnInitialUpdate();  
}  
```  
  
 记录集打开时会选择记录。  [CRecordset::Open](../Topic/CRecordset::Open.md) 或 [CDaoRecordset::Open](../Topic/CDaoRecordset::Open.md) 使第一条记录成为当前记录，DDX 将记录集字段数据成员的数据移至视图中相应的表单控件。  有关 RFX 的更多信息，请参阅[记录字段交换 \(RFX\)](../data/odbc/record-field-exchange-rfx.md)。  有关 DDX 的更多信息，请参阅[对话框数据交换和验证](../mfc/dialog-data-exchange-and-validation.md)。  有关文档\/视图创建流程的信息，请参阅[使用类编写 Windows 应用程序](../mfc/using-the-classes-to-write-applications-for-windows.md)。  
  
> [!NOTE]
>  你应使你的最终用户有能力刷新记录集的记录视图控件。  若没有此能力，当用户将控件的值更改为非法值时，用户可能会永远停滞在当前的记录。  若要刷新控件，请调用具有 **FALSE** 参数的 `CWnd` 成员函数 [UpdateData](../Topic/CWnd::UpdateData.md)。  
  
## 请参阅  
 [使用记录视图](../data/using-a-record-view-mfc-data-access.md)