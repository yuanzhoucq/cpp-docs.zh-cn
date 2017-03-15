---
title: "MFC 添加类向导 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.codewiz.class.mfc.simple.overview
dev_langs:
- C++
helpviewer_keywords:
- MFC Add Class Wizard
- wizards [MFC]
ms.assetid: ad3b0989-d307-43b2-9417-3f9a78889024
caps.latest.revision: 16
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 4fafe461008e3545243d693e0d9e34acd57163e0
ms.openlocfilehash: 08d258c2b8386a4dd0c1d24c6ac6aa10f6c04a63
ms.lasthandoff: 02/24/2017

---
# <a name="mfc-add-class-wizard"></a>MFC 添加类向导
若要向现有 MFC 项目中，添加一个类，或将类添加到支持 MFC 的 ATL 项目，请使用此代码向导。 此外可以具有的 MFC 支持的 Win32 项目的添加 MFC 类。 指定当您在创建项目时的功能确定在此对话框中可用的选项。  
  
## <a name="names"></a>名称  
 在此页上，指定的类名、 基类和新类的文件名。  
  
 **类名**  
 指定新类的名称，并提供默认基值 Id 和在此页上的文件的名称。 C + + 类通常开头"C"，例如，"CMyClass"变为"MyClass.h"，依次类推。  
  
 **基类**  
 指定新类的基类的名称。 默认情况下，基类是[CWnd](../../mfc/reference/cwnd-class.md)。 您选择的基类确定在此页上的其他框是否处于活动状态。  
  
 类类型的设置如基类决定类有对话框 ID 或资源 id。 常规类型的类如下所示︰  
  
-   类，如[CButton](../../mfc/reference/cbutton-class.md)， [CWnd](../../mfc/reference/cwnd-class.md)，或[CDocument](../../mfc/reference/cdocument-class.md)，不需要对话 ID 或资源 id。 这些类不使用对话框或资源 id。 如果您选择其中一个类作为基类，**对话框 ID**框和**DHTML 资源 ID**框灰显。  
  
-   类，如[CDialog](../../mfc/reference/cdialog-class.md)， [CFormView](../../mfc/reference/cformview-class.md)，或[CPropertyPage](../../mfc/reference/cpropertypage-class.md)，这需要一个对话框的 id。  
  
-   此类[CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md)，这需要对话框 ID、 DHTML 资源 ID 和 HTML 文件的名称。  
  
 对于需要对话框 ID 的类，您可能会发现它更高效地使用[资源编辑器](../../windows/resource-editors.md)若要创建对话框资源，其在中分配 ID[属性窗口](/visualstudio/ide/reference/properties-window)，然后创建一个具有该资源 ID 关联的类 请参阅[创建一个新对话框](../../windows/creating-a-new-dialog-box.md)有关创建标准的 Windows 对话框的详细信息。  
  
> [!NOTE]
>  如果您先创建对话框资源，派生其新的类从`CDHtmlDialog`，删除标准的 Windows**确定**和**取消**默认值对话框中显示的按钮。 标准的 Windows 对话框中承载 DHTML 窗体，其中包含其自身**确定**和**取消**按钮。  
  
 虽然 Windows 控件和 DHTML 控件可以包含对话框中，不建议。  
  
 **对话框 ID**  
 如果选择了指定的对话框中，ID `CDialog`， `CFormView`， `CPropertyPage`，或`CDHtmlDialog`作为**基类**。  
  
 **.h 文件**  
 设置新对象的类的头文件的名称。 默认情况下，此名称取决于您在中提供的名称**类名**。 单击省略号按钮以保存到您选择的位置的文件名称或类声明追加到现有文件。 如果您选择现有文件，该向导会将其保存到所选位置直到您单击**完成**在向导中。  
  
 该向导不会覆盖文件。 如果选择的名称的现有文件，则单击**完成**，向导会提示您指出类声明是否应追加到文件的内容。 单击**是**追加该文件; 单击**否**以返回到向导并指定其他文件名。  
  
 **.cpp 文件中**  
 设置新对象的类的实现文件的名称。 默认情况下，此名称取决于您在中提供的名称**类名**。 单击省略号按钮以将文件名称保存到您选择的位置。 该文件不保存到所选的位置，直到您单击**完成**在向导中。  
  
 该向导不会覆盖文件。 如果选择的名称的现有文件，则单击**完成**，向导会提示您指出类实现是否应追加到文件的内容。 单击**是**追加该文件; 单击**否**以返回到向导并指定其他文件名。  
  
 **活动辅助功能**  
 支持 MFC 的活动辅助功能通过调用[EnableActiveAccessibility](../../mfc/reference/cwnd-class.md#enableactiveaccessibility)构造函数中。 此选项才可用，派生的类从[CWnd](../../mfc/reference/cwnd-class.md)。  
  
 **DHTML 资源 ID**  
 将应用到类派生自`CDHtmlDialog`仅。 指定 DHTML 对话框中的资源 ID。 资源 ID 出现在项目的.rc 文件，以及 HTML 对话框框中文件名的 HTML 节。 此 id 标识的 DHTML 资源都由对话框中，由标识**对话框 ID**。  
  
 **.HTM 文件**  
 将应用到类派生自`CDHtmlDialog`仅。 设置 DHTML 对话框中的 HTML 文件的名称。 默认情况下，此文件名称取决于的类名。 该文件名将显示在 HTML 部分的项目的.rc 文件，以及 DHTML 对话框框中的资源 id。  
  
 **自动化**  
 设置对支持的类级别[自动化](../../mfc/automation.md)。 在类级别的自动化是可用于支持自动化的所有类。 它还是可用于创建带自动化支持的项目。 也就是说的 MFC 项目[支持 ATL](../../atl/reference/mfc-support-in-atl-projects.md)，为其选择的 MFC 项目或者**自动化**中的复选框[高级功能](../../mfc/reference/advanced-features-mfc-application-wizard.md)MFC 应用程序向导页。  
  
|选项|说明|  
|------------|-----------------|  
|**无**|指示类具有没有自动化支持。|  
|**自动化**|指示的类支持自动化。 如果选择此选项时，新创建的类可作为由自动化客户端应用程序，如 Microsoft Visual Basic 和 Microsoft Excel 的可编程对象。 此选项不可用于此表后面列出的基类。|  
|**可按类型 ID 创建**|表示类和项目支持其他应用程序创建使用自动化此类的对象。 使用此选项，自动化客户端可以直接创建自动化对象。 客户端应用程序使用在文本框中的 type ID 来指定要创建; 对象它是系统范围内，并必须是唯一的。 此选项不可用于此表后面列出的基类。|  
  
 自动化支持不可用的以下基本类︰  
  
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
 设置类的类型 ID。 **类型 ID**框连接项目名称和新的类名称，如下所示︰ *MFCProj.MFCClass*。 此 ID 才可以更改仅在选择**自动化**选项**可按类型 ID 创建**。  
  
 **生成 DocTemplate 资源**  
 指示由应用程序创建的文档的文档模板资源。 若要激活此复选框，该项目必须支持 MFC 文档/视图体系结构，并且此类的基类必须是[CFormView](../../mfc/reference/cformview-class.md)。  
  
 请参阅[文档模板和文档/视图创建过程](../../mfc/document-templates-and-the-document-view-creation-process.md)有关详细信息。  
  
## <a name="see-also"></a>另请参阅  
 [MFC 类](../../mfc/reference/adding-an-mfc-class.md)   
 [添加类](../../ide/adding-a-class-visual-cpp.md)

