---
title: MFC 添加类向导 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.codewiz.class.mfc.simple.overview
dev_langs:
- C++
helpviewer_keywords:
- MFC Add Class Wizard
- wizards [MFC]
ms.assetid: ad3b0989-d307-43b2-9417-3f9a78889024
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9560dec12a7710076f752d5329269c844f0d3a8b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33373406"
---
# <a name="mfc-add-class-wizard"></a>MFC 添加类向导
若要向现有 MFC 项目中，添加一个类，或将类添加到支持 MFC 的 ATL 项目，请使用此代码向导。 你还可以向具有 MFC 支持的 Win32 项目中添加 MFC 类。 创建你的项目时指定的功能确定在此对话框中可用的选项。  
  
## <a name="names"></a>名称  
 在此页上，指定类名，基类，以及为新类的文件名称。  
  
 **类名**  
 指定新类的名称并提供的默认基础的 Id 和在此页上的文件的名称。 C + + 类通常开头，"C"，例如，"CMyClass"变为"MyClass.h"，依次类推。  
  
 **基类**  
 指定新类的基类的名称。 默认情况下，类的基类是[CWnd](../../mfc/reference/cwnd-class.md)。 您选择的基本类确定是否在此页上的其他框处于活动状态。  
  
 类类型的设置，如基类确定此类具有对话框 ID 或资源 id。 常规类型的类如下所示：  
  
-   类，如[CButton](../../mfc/reference/cbutton-class.md)， [CWnd](../../mfc/reference/cwnd-class.md)，或[CDocument](../../mfc/reference/cdocument-class.md)，不需要一个对话框 ID 或资源 id。 这些类不使用对话框或资源 id。 如果你选择用于你的基类，这些类之一**对话框 ID**框和**DHTML 资源 ID**框变暗。  
  
-   类，如[CDialog](../../mfc/reference/cdialog-class.md)， [CFormView](../../mfc/reference/cformview-class.md)，或[CPropertyPage](../../mfc/reference/cpropertypage-class.md)，这需要对话框 id。  
  
-   类[CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md)，这要求对话框 ID、 DHTML 资源 ID 和 HTML 文件名称。  
  
 对于需要对话框 ID 的类，你可能会发现它使用更加高效[资源编辑器](../../windows/resource-editors.md)若要创建对话框资源，请将在其 ID 分配[属性窗口](/visualstudio/ide/reference/properties-window)，然后创建一个关联的类与该资源 id。 请参阅[创建新对话框](../../windows/creating-a-new-dialog-box.md)有关创建一个标准的 Windows 对话框的详细信息。  
  
> [!NOTE]
>  如果你先创建对话框资源，派生其新类从`CDHtmlDialog`，删除了标准的 Windows**确定**和**取消**出现在默认对话框的按钮。 标准的 Windows 对话框承载 DHTML 窗体中，包含其自有**确定**和**取消**按钮。  
  
 虽然 Windows 控件和 DHTML 控件，可以包含对话框中，不建议。  
  
 **对话框 ID**  
 指定的 ID 的对话框中，如果你选择`CDialog`， `CFormView`， `CPropertyPage`，或`CDHtmlDialog`作为**基类**。  
  
 **.h 文件**  
 设置新对象的类的头文件的名称。 默认情况下，此名称基于你在中提供的名称**类名**。 单击省略号按钮，以将文件名称保存到你选择的位置，或者将类声明追加到现有文件。 如果你选择现有文件，向导将不将其保存到所选位置直到你单击**完成**向导中。  
  
 向导不会覆盖文件。 如果选择的名称的现有文件，则单击**完成**，向导会提示您指出类声明是否应追加到文件的内容。 单击**是**要追加文件; 单击**否**返回到向导并指定另一个文件的名称。  
  
 **.cpp 文件**  
 设置新对象的类实现文件的名称。 默认情况下，此名称基于你在中提供的名称**类名**。 单击省略号按钮以将文件名称保存到你选择的位置。 文件不保存到选定的位置，直到您单击**完成**向导中。  
  
 向导不会覆盖文件。 如果选择的名称的现有文件，则单击**完成**，向导会提示您指出类实现是否应追加到文件的内容。 单击**是**要追加文件; 单击**否**返回到向导并指定另一个文件的名称。  
  
 **活动辅助功能**  
 启用通过调用对活动辅助功能的 MFC 的支持[EnableActiveAccessibility](../../mfc/reference/cwnd-class.md#enableactiveaccessibility)构造函数中。 此选项才可用类派生自[CWnd](../../mfc/reference/cwnd-class.md)。  
  
 **DHTML 资源 ID**  
 将应用到类派生自`CDHtmlDialog`仅。 指定 DHTML 对话框中的资源 ID。 资源 ID 将显示在项目的.rc 文件，以及 HTML 对话框框中的文件名称 HTML 部分。 DHTML 标识的资源，此 id，由托管对话框中，由标识**对话框 ID**。  
  
 **.HTM 文件**  
 将应用到类派生自`CDHtmlDialog`仅。 设置 DHTML 对话框中的 HTML 文件的名称。 默认情况下，此文件名基于类名称。 文件名称出现在 HTML 部分中的项目的.rc 文件，以及 DHTML 对话框框中的资源 id。  
  
 **自动化**  
 设置的支持的类级别[自动化](../../mfc/automation.md)。 在类级别的自动化是可用于支持自动化的所有类。 还有可用于创建带自动化支持的项目。 即，任一 MFC 项目[支持 ATL](../../atl/reference/mfc-support-in-atl-projects.md)，或为其选择的 MFC 项目**自动化**中的复选框[高级功能](../../mfc/reference/advanced-features-mfc-application-wizard.md)MFC 页应用程序向导。  
  
|选项|描述|  
|------------|-----------------|  
|**无**|指示此类具有不自动化支持。|  
|**自动化**|指示的类支持自动化。 如果选择此选项时，新创建的类将用作为由自动化客户端应用程序，如 Microsoft Visual Basic 和 Microsoft Excel 的可编程对象。 此选项不可用于此表后面列出的基类。|  
|**可按类型 ID 创建**|指示的类和项目支持创建对象，该类使用自动化的其他应用程序。 使用此选项，自动化客户端可以直接创建自动化对象。 客户端应用程序使用在文本框中的类型 ID 来指定要创建; 的对象它是系统级并且必须是唯一的。 此选项不可用于此表后面列出的基类。|  
  
 自动化的支持也无法供以下基类：  
  
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
 设置的类类型 ID。 **类型 ID**框将连接在一起的项目名称和新的类名称，如下所示： *MFCProj.MFCClass*。 此 ID 是仅当你选择可更改**自动化**选项**可按类型 ID 创建**。  
  
 **生成 DocTemplate 资源**  
 指示由应用程序创建的文档具有文档模板资源。 若要激活此复选框，项目必须支持 MFC 文档/视图体系结构，并且此类的基类必须是[CFormView](../../mfc/reference/cformview-class.md)。  
  
 请参阅[文档模板和文档/视图创建过程](../../mfc/document-templates-and-the-document-view-creation-process.md)有关详细信息。  
  
## <a name="see-also"></a>请参阅  
 [MFC 类](../../mfc/reference/adding-an-mfc-class.md)   
 [添加类](../../ide/adding-a-class-visual-cpp.md)
