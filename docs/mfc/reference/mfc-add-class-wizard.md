---
title: MFC 添加类向导
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.class.mfc.simple.overview
helpviewer_keywords:
- MFC Add Class Wizard
- wizards [MFC]
ms.assetid: ad3b0989-d307-43b2-9417-3f9a78889024
ms.openlocfilehash: 201f3f08e59dd9b252e0d008e61adea234449157
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50476318"
---
# <a name="mfc-add-class-wizard"></a>MFC 添加类向导

将类添加到现有 MFC 项目，或将一个类添加到 ATL 项目支持 MFC，请使用此代码向导。 您还可以向具有 MFC 支持的 Win32 项目添加 MFC 类。 创建你的项目时指定的功能确定在此对话框中可用的选项。

## <a name="names"></a>名称

在此页上，指定类名、 基类和新类的文件名。

- **类名**

   指定新类的名称并提供的默认基础的 Id 和在此页上的文件的名称。 C + + 类通常开始于"C"，因此，例如，"CMyClass"变为"MyClass.h"，依次类推。

- **基类**

   指定新类的基类的名称。 默认情况下，基类是[CWnd](../../mfc/reference/cwnd-class.md)。 您选择的基类确定其他框，在此页处于活动状态。

   类类型的设置，如类的基类确定类是否具有对话框 ID 或资源 id。 常规类型的类如下所示：

   - 类，如[CButton](../../mfc/reference/cbutton-class.md)， [CWnd](../../mfc/reference/cwnd-class.md)，或[CDocument](../../mfc/reference/cdocument-class.md)，这不需要对话 ID 或资源 id。 这些类不使用对话框或资源 id。 如果你选择的基类，这些类之一**对话框 ID**框和**DHTML 资源 ID**框灰显。

   - 类，如[CDialog](../../mfc/reference/cdialog-class.md)， [CFormView](../../mfc/reference/cformview-class.md)，或[CPropertyPage](../../mfc/reference/cpropertypage-class.md)，这需要一个对话框的 id。

   - 该类[CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md)，这需要对话框 ID、 DHTML 资源 ID 和 HTML 文件名称。

   对于需要对话框 ID 的类，你可能会发现它使用更高效[资源编辑器](../../windows/resource-editors.md)若要创建对话框资源，将分配在其 ID[属性窗口](/visualstudio/ide/reference/properties-window)，然后创建一个关联的类与该资源 id。 请参阅[创建一个新对话框](../../windows/creating-a-new-dialog-box.md)有关创建标准的 Windows 对话框的详细信息。

   > [!NOTE]
   > 如果你先创建对话框资源，派生从其新的类`CDHtmlDialog`，删除标准 Windows**确定**并**取消**默认对话框中显示的按钮。 标准 Windows 对话框承载 DHTML 窗体，其中包含其自身**确定**并**取消**按钮。

   尽管 Windows 控件和 DHTML 控件可以包含对话框中，不建议。

- **对话框 ID**

   如果选择了指定的对话框中，ID `CDialog`， `CFormView`， `CPropertyPage`，或`CDHtmlDialog`作为**基类**。

- **.h 文件**

   为新项目的类的头文件设置名称。 默认情况下，此名称基于你在“类名”中提供的名称。 单击省略号按钮以将该文件名保存至所选择的位置，或追加到某个现有文件的类声明中。 如果选择现有文件，则向导在你单击“完成”之前都不会将其保存至所选位置。

   向导不会覆盖文件。 如果选择现有文件的名称，当你单击“完成”时，向导会询问你是否要将该类声明追加至文件的内容中。 单击“是”，则追加该文件；单击“否”，则返回至向导并指定另一个文件名。

- **.cpp 文件**

   为新项目的类的实现文件设置名称。 默认情况下，此名称基于你在“类名”中提供的名称。 单击省略号按钮以将文件名保存到所选位置。 向导在你单击“完成”之前不会将该文件保存到所选位置。

   向导不会覆盖文件。 如果选择现有文件的名称，当你单击“完成”时，向导会询问你是否要将该类实现追加至文件的内容中。 单击“是”，则追加该文件；单击“否”，则返回至向导并指定另一个文件名。

- **活动辅助功能**

   通过调用使 MFC 的支持的 Active Accessibility [EnableActiveAccessibility](../../mfc/reference/cwnd-class.md#enableactiveaccessibility)构造函数中。 此选项才可用的类派生自[CWnd](../../mfc/reference/cwnd-class.md)。

- **DHTML 资源 ID**

   适用于从派生的类`CDHtmlDialog`仅。 指定 DHTML 对话框中的资源 ID。 项目的.rc 文件，以及 HTML 对话框框中的文件名称的 HTML 部分中显示的资源 ID。 此 id 标识的 DHTML 资源托管的对话框中，由标识**对话框 ID**。

- **.HTM 文件**

   适用于从派生的类`CDHtmlDialog`仅。 设置 DHTML 对话框中的 HTML 文件的名称。 默认情况下，此文件的名称基于类名称。 该文件名将显示在 HTML 部分中的项目的.rc 文件，以及 DHTML 对话框框中的资源 id。

- **自动化**

   设置类级别的支持[自动化](../../mfc/automation.md)。 在类级别的自动化是可用于支持自动化的所有类。 还有可用于创建具有自动化支持的项目。 也就是说的 MFC 项目的[支持 ATL](../../atl/reference/mfc-support-in-atl-projects.md)，或为其选择一个 MFC 项目**自动化**中的复选框[高级功能](../../mfc/reference/advanced-features-mfc-application-wizard.md)MFC 页应用程序向导。

   |选项|描述|
   |------------|-----------------|
   |**无**|指示类具有没有自动化的支持。|
   |**自动化**|指示该类支持自动化。 如果选择此选项时，新创建的类是作为自动化客户端应用程序，例如 Microsoft Visual Basic 和 Microsoft Excel 的可编程对象可用。 此选项不可用于此表后面列出的基类。|
   |**可创建对象的类型 ID**|表示的类和项目支持其他应用程序创建使用自动化此类的对象。 使用此选项时，自动化客户端可以直接创建自动化对象。 客户端应用程序使用在文本框中的类型 ID 来指定要创建; 的对象它是系统范围内并且必须是唯一的。 此选项不可用于此表后面列出的基类。|

   自动化的支持不可用于以下基类：

   - `CAsyncMonitorFile`

   - `CAsyncSocket`

   - `CCachedDataPathProperty`

   - `CConnectionPoint`

   - `CDatabase`

   - `CDataPathProperty`

   - `CHttpFilter`

   - `CHttpServer`

   - `CInternetSession`

   - `CObject`

   - `CSocket`

- **类型 ID**

   设置类的类型 ID。 **类型 ID**框连接项目名称和新的类名称，如下所示： *MFCProj.MFCClass*。 此 ID 是仅当你选择可更改**自动化**选项**可按类型 ID 创建**。

- **生成 DocTemplate 资源**

   指示应用程序创建的文档具有文档模板资源。 若要激活此复选框，该项目必须支持 MFC 文档/视图体系结构，并且必须是此类的基类[CFormView](../../mfc/reference/cformview-class.md)。

   请参阅[文档模板和文档/视图创建过程](../../mfc/document-templates-and-the-document-view-creation-process.md)有关详细信息。

## <a name="see-also"></a>请参阅

[MFC 类](../../mfc/reference/adding-an-mfc-class.md)<br/>
[添加类](../../ide/adding-a-class-visual-cpp.md)
