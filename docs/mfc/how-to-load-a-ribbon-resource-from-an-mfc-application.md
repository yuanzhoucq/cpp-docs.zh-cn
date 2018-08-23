---
title: 如何： 从 MFC 应用程序加载功能区资源 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ribbon resource [MFC], loading
ms.assetid: 1c76bb8f-6345-414a-9f3f-128815ceadc5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b014e1725ae6c5043c051242a74e29338c3ef2d6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33344186"
---
# <a name="how-to-load-a-ribbon-resource-from-an-mfc-application"></a>如何：从 MFC 应用程序中加载功能区资源
若要在应用程序中使用功能区资源，请修改应用程序以加载功能区资源。  
  
### <a name="to-load-a-ribbon-resource"></a>加载功能区资源  
  
1.  在 `Ribbon Control` 类中声明 `CMainFrame` 对象。  
  
 ```  
    CMFCRibbonBar m_wndRibbonBar;   
 ```  
  
2.  在 `CMainFrame::OnCreate` 中，创建并初始化功能区控件。  
  
 ```  
    if (!m_wndRibbonBar.Create (this))  
 {  
    return -1;  
 }  
 
    if (!m_wndRibbonBar.LoadFromResource(IDR_RIBBON))  
 {  
    return -1;  
 }  
 ```  
  
## <a name="see-also"></a>请参阅  
 [功能区设计器 (MFC)](../mfc/ribbon-designer-mfc.md)

