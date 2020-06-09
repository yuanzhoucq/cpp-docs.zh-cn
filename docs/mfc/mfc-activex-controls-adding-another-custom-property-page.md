---
title: MFC ActiveX 控件：添加另一自定义属性页
ms.date: 11/04/2016
helpviewer_keywords:
- property pages [MFC], MFC ActiveX controls
- custom property pages [MFC]
- ActiveX controls [MFC], property pages
- MFC ActiveX controls [MFC], property pages
ms.assetid: fcf7e119-9f29-41a9-908d-e9b1607e08af
ms.openlocfilehash: 33fd297ee509b341d39d9db21af54a3988f6256e
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618291"
---
# <a name="mfc-activex-controls-adding-another-custom-property-page"></a>MFC ActiveX 控件：添加另一自定义属性页

有时，ActiveX 控件的属性数比可合理容纳在一个属性页上的属性多。 在这种情况下，您可以将属性页添加到 ActiveX 控件以显示这些属性。

本文讨论如何向已至少具有一个属性页面的 ActiveX 控件添加新属性页。 有关添加常用属性页（字体、图片或颜色）的详细信息，请参阅[MFC ActiveX 控件：使用常用属性页](mfc-activex-controls-using-stock-property-pages.md)一文。

以下过程使用 ActiveX 控件向导创建的示例 ActiveX 控件框架。 因此，此示例中的类名称和标识符是唯一的。

有关在 ActiveX 控件中使用属性页的详细信息，请参阅以下文章：

- [MFC ActiveX 控件：属性页](mfc-activex-controls-property-pages.md)

- [MFC ActiveX 控件：使用常用属性页](mfc-activex-controls-using-stock-property-pages.md)

    > [!NOTE]
    >  强烈建议新属性页遵循 ActiveX 控件属性页的大小标准。 "股价图" 和 "颜色" 属性页度量250x62 对话框单位（DLU）。 标准字体属性页为 250x110 Dlu。 ActiveX 控件向导创建的默认属性页使用 250x62 DLU 标准。

### <a name="to-insert-a-new-property-page-template-into-your-project"></a>将新属性页模板插入到项目中

1. 打开控件项目后，打开 "项目" 工作区中的资源视图。

1. 右键单击资源视图打开快捷菜单，然后单击 "**添加资源**"。

1. 展开**对话框**节点，然后选择 " **IDD_OLE_PROPPAGE_SMALL**"。

1. 单击 "**新建**" 将资源添加到项目。

1. 选择 "新建" 属性页模板以刷新 "**属性**" 窗口（在**资源视图**中）。

1. 为 " **ID** " 属性输入新值。 此示例使用**IDD_PROPPAGE_NEWPAGE**。

1. 单击工具栏上的“保存”。****

### <a name="to-associate-the-new-template-with-a-class"></a>将新模板与类相关联

1. 打开类视图。

1. 右键单击 "类视图" 以打开快捷菜单。

1. 在快捷菜单中，依次单击“添加”**** 和“添加类”****。

   这将打开 "[添加类](../ide/add-class-dialog-box.md)" 对话框。

1. 双击 " **MFC 类**" 模板。

1. 在[MFC 类向导](reference/mfc-add-class-wizard.md)的 "**类名称**" 框中，键入新对话框类的名称。 （在此示例中为 `CAddtlPropPage` 。）

1. 如果要更改文件名，请单击 "**更改**"。 键入实现和标头文件的名称，或接受默认名称。

1. 在 "**基类**" 对话框中，选择 `COlePropertyPage` 。

1. 在**对话框**中，选择 " **IDD_PROPPAGE_NEWPAGE**"。

1. 单击 "**完成**" 以创建类。

若要允许控件的用户访问此新属性页，请对控件的属性页 Id 宏部分（位于控件实现文件中）进行以下更改：

[!code-cpp[NVC_MFC_AxUI#32](codesnippet/cpp/mfc-activex-controls-adding-another-custom-property-page_1.cpp)]

请注意，必须将 BEGIN_PROPPAGEIDS 宏的第二个参数（属性页计数）从1增加到2。

还必须修改控件实现文件（。CPP）文件来包含标头（。H）文件。

接下来的步骤涉及创建两个新的字符串资源，这些资源将为新属性页提供类型名称和标题。

#### <a name="to-add-new-string-resources-to-a-property-page"></a>向属性页中添加新的字符串资源

1. 打开控件项目后，打开资源视图。

1. 双击 "**字符串表**" 文件夹，然后双击要向其添加字符串的现有字符串表资源。

   这会在窗口中打开字符串表。

1. 选择字符串表末尾的空行，然后键入字符串的文本或标题，例如 "附加属性页"。

   这会打开一个显示 "**标题**" 和 " **ID** " 框的**字符串 "属性**" 页。 "**标题**" 框包含您键入的字符串。

1. 在 " **id** " 框中，选择或键入字符串的 ID。 完成后，按 Enter。

   此示例使用新属性页的类型名称**IDS_SAMPLE_ADDPAGE** 。

1. 使用 "ID" **IDS_SAMPLE_ADDPPG_CAPTION**和 "附加属性页" 作为标题，重复步骤3和4。

1. 在。新属性页类的 CPP 文件（在此示例中 `CAddtlPropPage` ）修改， `CAddtlPropPage::CAddtlPropPageFactory::UpdateRegistry` 以便[AfxOleRegisterPropertyPageClass](reference/registering-ole-controls.md#afxoleregisterpropertypageclass)传递 IDS_SAMPLE_ADDPAGE，如以下示例中所示：

   [!code-cpp[NVC_MFC_AxUI#33](codesnippet/cpp/mfc-activex-controls-adding-another-custom-property-page_2.cpp)]

1. 修改的构造函数 `CAddtlPropPage` ，以便将 IDS_SAMPLE_ADDPPG_CAPTION 传递给 `COlePropertyPage` 构造函数，如下所示：

   [!code-cpp[NVC_MFC_AxUI#34](codesnippet/cpp/mfc-activex-controls-adding-another-custom-property-page_3.cpp)]

进行所需修改后，重新生成项目，并使用测试容器来测试新属性页。 请参阅 [使用测试容器测试属性和事件](testing-properties-and-events-with-test-container.md) 了解有关如何访问测试容器的信息。

## <a name="see-also"></a>另请参阅

[MFC ActiveX 控件](mfc-activex-controls.md)
