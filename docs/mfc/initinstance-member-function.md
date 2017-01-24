---
title: "InitInstance 成员函数 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "InitInstance"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "应用程序 [MFC], 初始化"
  - "初始化 MFC 应用程序"
  - "InitInstance 方法"
  - "MFC [C++], 初始化"
ms.assetid: 4ef09267-ff7f-4c39-91a0-57454a264f83
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# InitInstance 成员函数
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Windows 操作系统允许您运行多个实例或“复制”，同一应用程序。  `WinMain` 调用 [InitInstance](../Topic/CWinApp::InitInstance.md)，在应用程序启动的新实例时。  
  
 MFC 应用程序向导创建标准的 `InitInstance` 实现可执行下列任务：  
  
-   作为其中枢效果，与创建创建文档、视图和文档模板的框架窗口。  有关此过程的说明，请参见 [创建文档模板](../mfc/document-template-creation.md)。  
  
-   从负载的 .ini 文件或 Windows 注册表的标准文件选项，其中最近使用的文件的名称。  
  
-   注册一个或多个文档模板。  
  
-   在 MDI 应用程序，若要创建主框架窗口。  
  
-   处理命令行上打开命令行指定的文档或打开新，空文档。  
  
 您可以添加自己初始化代码或修改向导编写的代码。  
  
> [!NOTE]
>  MFC应用程序必须被初始化为单线程单元（STA）。  如果在 `InitInstance` 重写时调用 [CoInitializeEx](http://msdn.microsoft.com/library/windows/desktop/ms695279) ，请指定 `COINIT_APARTMENTTHREADED` （而不是 `COINIT_MULTITHREADED`）。  有关详细信息，请参阅 PRB: 当在 [http:\/\/support.microsoft.com\/default.aspx?scid\=kb;en\-us;828643](http://support.microsoft.com/default.aspx?scid=kb;en-us;828643) 初始化应用程序为多线程单元（828643）时，MFC应用程序停止响应。  
  
## 请参阅  
 [CWinApp：应用程序类](../mfc/cwinapp-the-application-class.md)