---
title: "MFC 添加类向导 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.codewiz.class.mfc.simple.overview"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MFC 添加类向导"
  - "向导 [MFC]"
ms.assetid: ad3b0989-d307-43b2-9417-3f9a78889024
caps.latest.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 16
---
# MFC 添加类向导
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用此代码向导将类添加到现有的 MFC 项目，或将类添加到支持 MFC 的 ATL 项目。  也可以将 MFC 类添加到具有 MFC 支持的 Win32 项目中。  创建项目时指定的功能决定此对话框中的可用选项。  
  
## 名称  
 在该页中，指定新类的类名、基类和文件名。  
  
 **类名**  
 指定新类的名称，并为该页上的 ID 和文件的名称提供默认基础。  C\+\+ 类通常以“C”开头，所以，对于 CMyClass，可为 MyClass.h，依此类推。  
  
 **基类**  
 指定新类的基类名称。  默认情况下，基类为 [CWnd](../../mfc/reference/cwnd-class.md)。  选定的基类决定该页上的其他框是否活动。  
  
 设为基类的类类型决定了类是否有对话框 ID 或资源 ID。  常规类类型如下所示：  
  
-   诸如 [CButton](../../mfc/reference/cbutton-class.md)、[CWnd](../../mfc/reference/cwnd-class.md) 或 [CDocument](../../mfc/reference/cdocument-class.md) 的类，这些类不需要对话框 ID 或资源 ID。  这些类不使用对话框 ID 或资源 ID。  如果选择其中一个类作为基类，则“对话框 ID”框和“DHTML 资源 ID”框将灰显。  
  
-   诸如 [CDialog](../../mfc/reference/cdialog-class.md)、[CFormView](../../mfc/reference/cformview-class.md) 或 [CPropertyPage](../../mfc/reference/cpropertypage-class.md) 的类需要对话框 ID。  
  
-   [CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md) 类需要对话框 ID、DHTML 资源 ID 和 HTML 文件名。  
  
 对于需要对话框 ID 的类，您可能会发现以下方法更有效：用[资源编辑器](../../mfc/resource-editors.md)创建对话框资源，在[“属性”窗口](../Topic/Properties%20Window.md)中分配它的 ID，然后创建与资源 ID 关联的类。  有关创建标准 Windows 对话框的更多信息，请参见[创建新对话框](../../mfc/creating-a-new-dialog-box.md)。  
  
> [!NOTE]
>  如果先创建对话框资源并从 `CDHtmlDialog` 派生它的新类，则删除显示在默认对话框上的标准 Windows**“确定”**和“取消”按钮。  标准 Windows 对话框承载 DHTML 窗体，这类窗体包含自己的**“确定”**和“取消”按钮。  
  
 虽然对话框可以同时包含 Windows 控件和 DHTML 控件，但不建议这样做。  
  
 **对话框 ID**  
 如果选择了 `CDialog`、`CFormView`、`CPropertyPage` 或 `CDHtmlDialog` 作为“基类”，指定对话框的 ID。  
  
 **.h 文件**  
 为新对象的类设置头文件的名称。  默认情况下，此名称基于在“类名”中提供的名称。  单击省略号按钮将该文件名保存到所选位置，或将类声明追加到现有文件。  如果选择现有文件，则直到在向导中单击**“完成”**时，向导才将其保存到所选位置。  
  
 向导不覆盖文件。  如果选择现有文件的名称，则单击**“完成”**时，向导会提示您指出是否应向该文件的内容中追加类声明。  单击**“是”**追加该文件；单击**“否”**返回到向导并指定另一个文件名。  
  
 **.cpp 文件**  
 为新对象的类设置实现文件的名称。  默认情况下，此名称基于在“类名”中提供的名称。  单击省略号按钮将文件名保存到所选位置。  直到在向导中单击**“完成”**时，该文件才保存到所选位置。  
  
 向导不覆盖文件。  如果选择现有文件的名称，则单击**“完成”**时，向导会提示您指出是否应向该文件的内容中追加类实现。  单击**“是”**追加该文件；单击**“否”**返回到向导并指定另一个文件名。  
  
 **Active Accessibility**  
 通过调用构造函数中的 [EnableActiveAccessibility](../Topic/CWnd::EnableActiveAccessibility.md) 来启用 MFC 对 Active Accessibility 的支持。  此选项对从 [CWnd](../../mfc/reference/cwnd-class.md) 导出的类可用。  
  
 **DHTML 资源 ID**  
 仅应用于从 `CDHtmlDialog` 导出的类。  指定 DHTML 对话框的资源 ID。  资源 ID 与 HTML 对话框文件名一起显示在项目 .rc 文件的 HTML 节中。  此 ID 标识的 DHTML 资源由 **Dialog ID** 标识的对话框加载。  
  
 **.HTM 文件**  
 仅应用于从 `CDHtmlDialog` 导出的类。  设置 DHTML 对话框的 HTML 文件名。  默认情况下，此文件名基于类名。  此文件名与 DHTML 对话框资源 ID 一起显示在项目 .rc 文件的 HTML 节中。  
  
 **自动化**  
 设置[自动化](../../mfc/automation.md)支持的类级别。  对于所有支持自动化的类，类级别的自动化可用于所有支持自动化的类。  它还可用于以自动化支持创建的项目。  即，[支持 ATL](../../atl/reference/mfc-support-in-atl-projects.md) 的 MFC 项目或者在“MFC 应用程序向导”的[高级功能](../../mfc/reference/advanced-features-mfc-application-wizard.md)页中为其选择**“自动化”**复选框的 MFC 项目。  
  
|选项|说明|  
|--------|--------|  
|**无**|指示类没有自动化支持。|  
|**自动化**|指示类支持自动化。  如果选择此选项，新创建的类可被自动化客户端应用程序（如 Microsoft Visual Basic 和 Microsoft Excel）用作可编程对象。  此选项对于此表后列出的基类不可用。|  
|**可按类型 ID 创建**|指示类和项目都支持使用自动化创建此类的对象的其他应用程序。  使用此选项，自动化客户端可以直接创建自动化对象。  客户端应用程序使用此文本框中的类型 ID 指定要创建的对象；该类型 ID 是系统级内的并且必须唯一。  此选项对于此表后列出的基类不可用。|  
  
 自动化支持对以下基类不可用：  
  
-   `CAsyncMonitorFile`  
  
-   `CAsyncSocket`  
  
-   `CCachedDataPathProperty`  
  
-   `CConnectionPoint`  
  
-   `CDatabase`  
  
-   `CDataPathProperty`  
  
-   `CHttpFilter`  
  
-   `CHttpServer`  
  
-   `CInternetSession`  
  
-   `CObject`  
  
-   `CSocket`  
  
 **类型 ID**  
 设置类的类型 ID。  **“类型 ID”**框将项目名和新的类名连接为如下形式：*MFCProj.MFCClass*。  只有在选择了“自动化”选项“可按类型 ID 创建”时，此 ID 才可以更改。  
  
 **生成 DocTemplate 资源**  
 指示应用程序创建的文档具有文档模板资源。  为激活此复选框，项目必须支持 MFC 文档\/视图结构，并且该类的基类必须是 [CFormView](../../mfc/reference/cformview-class.md)。  
  
 有关更多信息，请参见[文档模板和文档\/视图的创建过程](../../mfc/document-templates-and-the-document-view-creation-process.md)。  
  
## 请参阅  
 [MFC 类](../../mfc/reference/adding-an-mfc-class.md)   
 [添加类](../../ide/adding-a-class-visual-cpp.md)