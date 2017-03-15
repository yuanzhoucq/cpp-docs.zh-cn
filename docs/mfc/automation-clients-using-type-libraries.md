---
title: "自动化客户端：使用类型库 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MkTypLib"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".odl 文件"
  - "自动化客户端, 类型库"
  - "类 [C++], 调度"
  - "客户端, 自动化"
  - "调度类"
  - "MkTypLib 工具"
  - "ODL（对象描述语言）"
  - "ODL 文件"
  - "类型库, 自动化客户端"
ms.assetid: d405bc47-118d-4786-b371-920d035b2047
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# 自动化客户端：使用类型库
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果客户端操作的服务器对象，自动化客户必须包含有关服务器对象的属性和方法的信息。  属性具有数据类型；方法通常返回值和参数接受。  客户端需要有关所有数据类型的信息的静态绑定到这些服务器对象类型。  
  
 此类型传递信息可以采用多种方法。  建议的方法是创建类型库。  
  
 有关 [MkTypLib](http://msdn.microsoft.com/library/windows/desktop/aa366797)的信息，请参见 [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)]。  
  
 Visual C\+\+ 可读取类型库文件和创建从 [COleDispatchDriver](../mfc/reference/coledispatchdriver-class.md)计划派生的类。  该类对象\) 这些服务器对象的属性和操作。  应用程序调用此对象的属性设置和操作，因此，从 `COleDispatchDriver` 继承的功能发送这些调用 OLE 系统，然后发送到服务器对象。  
  
 Visual C\+\+ 会自动维护了此类型库文件，则选择。包括自动化，在创建项目。  在每个生成一部分，将生成与 MkTypLib .tlb 文件。  
  
### 创建计划类从类型库 \(.tlb\) 文件  
  
1.  在类视图或解决方案资源管理器中，右击该项目并单击 **添加** 然后在快捷菜单中单击 **添加类**。  
  
2.  在 **添加类** 对话框中，选择左窗格中的 **Visual C\+\+\/MFC** 文件夹。  选择从右窗格中的 **TypeLib 中的 MFC 类** 图标并单击 **打开**。  
  
3.  在 **从类型库添加类向导** 对话框中，从 **Available type libraries** 下拉列表的类型库。  **接口** 框显示接口可用于选择的类型库。  
  
    > [!NOTE]
    >  可以选择从多个类型库的接口。  
  
     选择接口，双击其或单击 **添加** 按钮。  当您这样，名称调度类将显示在 **Generated classes** 框。  您可以编辑 `Class` 框的类名。  
  
     **文件** 框显示类将声明的文件。\(您可以编辑此文件名\)。  如果愿意在目录和实现信息编写中的现有文件或标头为项目目录外，还可以用来浏览按钮选择其他文件。  
  
    > [!NOTE]
    >  选择接口的所有调度类将被放入指定的文件在此处。  如果在单独的头需要接口声明，您必须对要创建的每个头文件使用此向导。  
  
    > [!NOTE]
    >  某些类型库信息以 .DLL、.ocx 或 .OLB 文件扩展名的文件可以存储。  
  
4.  单击**“完成”**。  
  
     使用指定类和文件名，向导将编写调度类的代码。  
  
## 请参阅  
 [自动化客户端](../mfc/automation-clients.md)