---
title: "创建活动文档容器应用程序 | Microsoft Docs"
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
  - "活动文档容器 [C++], 创建"
  - "活动文档 [C++], 容器"
  - "应用程序 [MFC], 活动文档容器"
  - "容器 [C++], 活动文档"
  - "MFC COM [C++], 活动文档包容"
ms.assetid: 14e2d022-a6c5-4249-8712-706b0f4433f7
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 创建活动文档容器应用程序
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

最简单且建议的方法到创建活动文档容器应用程序是创建 EXE MFC 容器应用程序，使用 MFC 应用程序向导，然后修改应用程序支持包容活动文档。  
  
#### 创建活动文档容器应用程序  
  
1.  从 **文件** 菜单中，从**新建** 子菜单上单击**项目** 。  
  
2.  从左窗格中，单击 **Visual C\+\+** 项目类型。  
  
3.  从右窗格中选择 **MFC 应用程序**。  
  
4.  将该项目命名为 `MyProj`，单击 **OK**。  
  
5.  选择 **复合文档支持** 页。  
  
6.  选择 **容器** 或 **Container\/Full\-server** 选项。  
  
7.  选择 **活动文档容器**  复选框。  
  
8.  单击**“完成”**。  
  
9. 当MFC 应用程序向导完成应用生成时，使用解决方案资源管理器打开下列文件：  
  
    -   MyProjview.cpp  
  
10. 在 MyProjview.cpp，请进行以下更改：  
  
    -   在 `CMyProjView::OnPreparePrinting`中，用下列代码替换文件的内容：  
  
         [!code-cpp[NVC_MFCDocView#56](../mfc/codesnippet/CPP/creating-an-active-document-container-application_1.cpp)]  
  
     `OnPreparePrinting` 提供打印支持。  此代码替换 `DoPreparePrinting`，这是默认打印准备。  
  
     活动文档包容提供了改进的打印方案：  
  
    -   通过其 `IPrint`接口可以在首次调用活动文档并将其打印。  这与前 OLE 包容不同，容器必须呈现包含图像的项到打印机 `CDC`对象上。  
  
    -   如果失败，请通知包含的项通过其 `IOleCommandTarget`接口打印  
  
    -   如果失败，使项自行呈现。  
  
     如前面代码中实现的，静态成员函数 `COleDocObjectItem::OnPrint` 和 `COleDocObjectItem::OnPreparePrinting`处理改进的打印方案。  
  
11. 添加所有自己的并生成应用程序。  
  
## 请参阅  
 [活动文档包容](../mfc/active-document-containment.md)