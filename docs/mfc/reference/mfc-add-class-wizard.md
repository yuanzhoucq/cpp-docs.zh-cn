---
title: MFC 添加类向导
ms.date: 09/06/2019
f1_keywords:
- vc.codewiz.class.mfc.simple.overview
helpviewer_keywords:
- MFC Add Class Wizard
- wizards [MFC]
ms.assetid: ad3b0989-d307-43b2-9417-3f9a78889024
ms.openlocfilehash: 2c82e084de2123c579299ca6490bdfcfdac5d255
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/11/2019
ms.locfileid: "70908013"
---
# <a name="mfc-add-class-wizard"></a>MFC 添加类向导

使用此代码向导可向现有 MFC 项目添加类，或将类添加到支持 MFC 的 ATL 项目。 还可以将 MFC 类添加到具有 MFC 支持的 Win32 项目。 创建项目时指定的功能将决定此对话框中的可用选项。 若要访问该向导，请单击 "在[类](mfc-class-wizard.md)中**添加类**向导"。

![添加 MFC 类向导](media/add-mfc-class-wizard.png "添加 MFC 类向导")

## <a name="names"></a>名称

在此页中，为新类指定类名、基类和文件名。

- **类名**

  指定新类的名称，并为此页上的 Id 和文件的名称提供默认基础。 C++类通常以 "C" 开头，因此，"CMyClass" 将变为 "MyClass" 等。

- **基类**

  指定新类的基类的名称。 默认情况下，基类为[CWnd](../../mfc/reference/cwnd-class.md)。 您选择的基类确定此页上的其他框是否处于活动状态。

  设置为基类的类的类型决定了此类是否具有对话框 ID 或资源 ID。 类的常规类型如下：

  - [CButton](../../mfc/reference/cbutton-class.md)、 [CWnd](../../mfc/reference/cwnd-class.md)或[CDocument](../../mfc/reference/cdocument-class.md)等类，它们不需要对话框 id 或资源 id。 这些类不使用对话框或资源 ID。 如果为基类选择了其中一个类，则**对话框 id**框和**DHTML 资源 ID**框将灰显。

  - 需要对话框 ID 的类，如[CDialog](../../mfc/reference/cdialog-class.md)、 [CFormView](../../mfc/reference/cformview-class.md)或[CPropertyPage](../../mfc/reference/cpropertypage-class.md)。

  - 类[CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md)，它需要一个对话框 ID、一个 DHTML 资源 ID 和一个 HTML 文件名。

  对于需要对话框 ID 的类，您可能会发现，使用[资源编辑器](../../windows/resource-editors.md)创建对话框资源、在[类向导](mfc-class-wizard.md)中分配其 ID，然后创建与该资源 ID 关联的类更有效。 有关创建标准 Windows 对话框的详细信息，请参阅[创建新对话框](../../windows/creating-a-new-dialog-box.md)。

  > [!NOTE]
  > 如果首先创建一个对话框资源并从`CDHtmlDialog`其派生新类，请删除 "默认" 对话框中显示的标准 Windows **"确定" 和 "** **取消**" 按钮。 标准 Windows 对话框承载 DHTML 窗体，该窗体包含其自己的 **"确定" 和 "** **取消**" 按钮。

  虽然对话框可以同时包含 Windows 控件和 DHTML 控件，但不建议这样做。

- **对话框 ID**

  如果选择`CDialog`了、 `CFormView`、 `CPropertyPage`或`CDHtmlDialog`作为**基类**，则指定对话框的 ID。

- **.h 文件**

  为新项目的类的头文件设置名称。 默认情况下，此名称基于你在“类名”中提供的名称。 单击省略号按钮以将该文件名保存至所选择的位置，或追加到某个现有文件的类声明中。 如果选择现有文件，则向导在你单击“完成”之前都不会将其保存至所选位置。

  向导不会覆盖文件。 如果选择现有文件的名称，当你单击“完成”时，向导会询问你是否要将该类声明追加至文件的内容中。 单击“是”，则追加该文件；单击“否”，则返回至向导并指定另一个文件名。

- **.cpp 文件**

  为新项目的类的实现文件设置名称。 默认情况下，此名称基于你在“类名”中提供的名称。 单击省略号按钮以将文件名保存到所选位置。 向导在你单击“完成”之前不会将该文件保存到所选位置。

  向导不会覆盖文件。 如果选择现有文件的名称，当你单击“完成”时，向导会询问你是否要将该类实现追加至文件的内容中。 单击“是”，则追加该文件；单击“否”，则返回至向导并指定另一个文件名。

- **可用辅助功能**

  通过在构造函数中调用[EnableActiveAccessibility](../../mfc/reference/cwnd-class.md#enableactiveaccessibility) ，启用 MFC 对 Active Accessibility 的支持。 此选项可用于从[CWnd](../../mfc/reference/cwnd-class.md)派生的类。

- **自动化**

  为[自动化](../../mfc/automation.md)设置类支持的级别。 类级别的自动化可用于支持自动化的所有类。 它还可用于以自动化的支持创建的项目。 即，[支持 ATL](../../atl/reference/mfc-support-in-atl-projects.md)的 mfc 项目，或在 Mfc 应用程序向导的 "[高级功能](../../mfc/reference/advanced-features-mfc-application-wizard.md)" 页中为其选择了 "**自动化**" 复选框的 mfc 项目。

   自动化支持不可用于以下基类：

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

## <a name="see-also"></a>请参阅

[MFC 类](../../mfc/reference/adding-an-mfc-class.md)<br/>
[添加类](../../ide/adding-a-class-visual-cpp.md)
