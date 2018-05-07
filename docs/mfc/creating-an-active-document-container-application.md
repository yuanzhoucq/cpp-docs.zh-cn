---
title: 创建活动文档容器应用程序 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- active documents [MFC], containers
- containers [MFC], active document
- active document containers [MFC], creating
- MFC COM, active document containment
- applications [MFC], active document container
ms.assetid: 14e2d022-a6c5-4249-8712-706b0f4433f7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 880c6953addd0ec7db3abf5864010bd472d2d5a3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="creating-an-active-document-container-application"></a>创建活动文档容器应用程序
最简单、最受推崇的活动文档容器应用程序的创建方式为使用 MFC 应用程序向导创建 MFC EXE 容器应用程序，然后将应用程序修改为支持活动文档包容。  
  
#### <a name="to-create-an-active-document-container-application"></a>创建活动文档容器应用程序  
  
1.  从**文件**菜单上，单击**项目**从**新建**子菜单。  
  
2.  从左窗格中，单击**Visual c + +** 项目类型。  
  
3.  选择**MFC 应用程序**右窗格中。  
  
4.  将项目`MyProj`，单击**确定**。  
  
5.  选择**复合文档支持**页。  
  
6.  选择**容器**或**容器/完全服务器**选项。  
  
7.  选择**活动文档容器**复选框。  
  
8.  单击 **“完成”**。  
  
9. 当 MFC 应用程序向导完成应用程序生成时，使用解决方案资源管理器打开下列文件：  
  
    -   MyProjview.cpp  
  
10. 在 MyProjview.cpp 中，进行下列更改：  
  
    -   在 `CMyProjView::OnPreparePrinting` 中，将函数内容替换为下列代码：  
  
         [!code-cpp[NVC_MFCDocView#56](../mfc/codesnippet/cpp/creating-an-active-document-container-application_1.cpp)]  
  
     `OnPreparePrinting` 将提供打印支持。 此代码将替换 `DoPreparePrinting`，其是默认打印准备。  
  
     活动文档包容将提供改进的打印方案：  
  
    -   您可以先调用活动文档通过其`IPrint`接口，并告诉它进行打印。 这是不同于以前的 OLE 包容，容器不得不呈现到打印机上包含的项的图像`CDC`对象。  
  
    -   如果失败，告诉所含的项以打印本身通过其`IOleCommandTarget`接口  
  
    -   如果失败，自行呈现项目。  
  
     如之前的代码所实现的一样，`COleDocObjectItem::OnPrint` 和 `COleDocObjectItem::OnPreparePrinting` 将处理此改进的打印方案。  
  
11. 添加您自己的任何实现并生成应用程序。  
  
## <a name="see-also"></a>请参阅  
 [活动文档包容](../mfc/active-document-containment.md)

