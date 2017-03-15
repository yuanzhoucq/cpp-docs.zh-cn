---
title: "MFC ActiveX 控件：创建自动化服务器 | Microsoft Docs"
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
  - "ActiveX 控件 [C++], 自动化服务器"
  - "自动化服务器 [C++], MFC ActiveX 控件"
  - "MFC ActiveX 控件 [C++], 自动化服务器"
ms.assetid: e0c24ed2-d61c-49ad-a4fa-4e1098d1d39b
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# MFC ActiveX 控件：创建自动化服务器
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可以开发 MFC ActiveX 控件用作自动化服务器用于嵌入程序设计应用程序中的控件中调用控件的方法的用途从应用程序。  此类控件中可用承载 ActiveX 控件容器。  
  
### 创建用作自动化服务器控件  
  
1.  [创建](../mfc/reference/mfc-activex-control-wizard.md) 控件。  
  
2.  [添加方法](../mfc/mfc-activex-controls-methods.md)。  
  
3.  重写 [IsInvokeAllowed](../Topic/COleControl::IsInvokeAllowed.md)。  有关更多信息，请参见知识库文章 Q146120。  
  
4.  生成控件。  
  
### 以编程方式访问在自动化服务器的方法  
  
1.  创建应用程序，例如，[MFC exe](../mfc/reference/mfc-application-wizard.md)。  
  
2.  在 `InitInstance` 函数开头，添加下面的代码行：  
  
     [!code-cpp[NVC_MFC_AxCont#17](../mfc/codesnippet/CPP/mfc-activex-controls-creating-an-automation-server_1.cpp)]  
  
3.  在"类视图"中，右击项目节点并选择 **Add class from typelib** 导入类型库。  
  
     这将添加 .h 和 .cpp 具有文件扩展名的文件添加到项目中。  
  
4.  在将在 ActiveX 控件的一个或多个方法，添加下列行类的头文件：，其中 `#include filename.h`为文件名创建头文件的名称，在导入类型库。  
  
5.  在电话将对在 ActiveX 控件中的方法相关的函数中，添加创建控件的包装类对象的代码并创建 ActiveX 对象。  例如，在按钮，在对话框后，单击下列 MFC 代码实例化 `CCirc` 控件，则获取标题属性，并显示结果：  
  
     [!code-cpp[NVC_MFC_AxCont#18](../mfc/codesnippet/CPP/mfc-activex-controls-creating-an-automation-server_2.cpp)]  
  
 如果添加方法到 ActiveX 控件，才能在应用程序中使用它，您可以开始使用控件的最新版本应用程序中通过删除创建的文件，当您导入类型库。  然后再次导入类型库。  
  
## 请参阅  
 [MFC ActiveX 控件](../mfc/mfc-activex-controls.md)