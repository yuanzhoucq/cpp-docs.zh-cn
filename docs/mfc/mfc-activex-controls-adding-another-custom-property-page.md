---
title: MFC ActiveX 控件：添加另一自定义属性页
ms.date: 11/04/2016
helpviewer_keywords:
- property pages [MFC], MFC ActiveX controls
- custom property pages [MFC]
- ActiveX controls [MFC], property pages
- MFC ActiveX controls [MFC], property pages
ms.assetid: fcf7e119-9f29-41a9-908d-e9b1607e08af
ms.openlocfilehash: 02c87c2c5283b7293c2a7ab028ec9a2abbba2b33
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364743"
---
# <a name="mfc-activex-controls-adding-another-custom-property-page"></a>MFC ActiveX 控件：添加另一自定义属性页

有时，ActiveX 控件的属性将超过一个属性页上的合理拟合属性。 在这种情况下，您可以将属性页添加到 ActiveX 控件以显示这些属性。

本文讨论将新属性页添加到已具有至少一个属性页的 ActiveX 控件。 有关添加股票属性页（字体、图片或颜色）的详细信息，请参阅文章[MFC ActiveX 控件：使用股票属性页](../mfc/mfc-activex-controls-using-stock-property-pages.md)。

以下过程使用由 ActiveX 控制向导创建的示例 ActiveX 控制框架。 因此，类名称和标识符是此示例所独有的。

有关在 ActiveX 控件中使用属性页的详细信息，请参阅以下文章：

- [MFC ActiveX 控件：属性页](../mfc/mfc-activex-controls-property-pages.md)

- [MFC ActiveX 控件：使用常用属性页](../mfc/mfc-activex-controls-using-stock-property-pages.md)

    > [!NOTE]
    >  强烈建议新属性页符合 ActiveX 控件属性页的大小标准。 库存图片和颜色属性页测量 250x62 对话框单元 （DLU）。 标准字体属性页为 250x110 DLL。 ActiveX 控件向导创建的默认属性页使用 250x62 DLU 标准。

### <a name="to-insert-a-new-property-page-template-into-your-project"></a>将新的属性页模板插入到项目中

1. 打开控件项目后，在项目工作区中打开资源视图。

1. 右键单击"资源视图"以打开快捷菜单，然后单击"**添加资源**"。

1. 展开**对话框**节点，然后选择**IDD_OLE_PROPPAGE_SMALL**。

1. 单击 **"新建**"以将资源添加到项目中。

1. 选择新的属性页模板以刷新**属性**窗口（在**资源视图中**）。

1. 输入**ID**属性的新值。 此示例使用**IDD_PROPPAGE_NEWPAGE**。

1. 单击工具栏上的“保存”。****

### <a name="to-associate-the-new-template-with-a-class"></a>将新模板与类关联

1. 打开类视图。

1. 在"类视图"中右键单击以打开快捷菜单。

1. 在快捷菜单中，依次单击“添加”**** 和“添加类”****。

   这将打开["添加类"](../ide/add-class-dialog-box.md)对话框。

1. 双击**MFC 类**模板。

1. 在[MFC 类向导](../mfc/reference/mfc-add-class-wizard.md)中的 **"类名称**"框中，键入新对话框类的名称。 （在此示例中，.） `CAddtlPropPage`

1. 如果要更改文件名，请单击"**更改**"。 键入实现和标头文件的名称，或接受默认名称。

1. 在 **"基本类"** 框中，`COlePropertyPage`选择 。

1. 在 **"对话框 ID"** 框中，选择**IDD_PROPPAGE_NEWPAGE**。

1. 单击 **"完成"** 以创建类。

要允许控件的用户访问此新属性页，请对控件的属性页 IDs 宏部分（位于控件实现文件中）进行以下更改：

[!code-cpp[NVC_MFC_AxUI#32](../mfc/codesnippet/cpp/mfc-activex-controls-adding-another-custom-property-page_1.cpp)]

请注意，必须将BEGIN_PROPPAGEIDS宏的第二个参数（属性页计数）从 1 增加到 2。

还必须修改控件实现文件 （。CPP 文件以包括标头 （。H） 新属性页类的文件。

下一步是创建两个新的字符串资源，为新属性页提供类型名称和标题。

#### <a name="to-add-new-string-resources-to-a-property-page"></a>向属性页添加新字符串资源

1. 打开控制项目后，打开资源视图。

1. 双击**字符串表**文件夹，然后双击要向其添加字符串的现有字符串表资源。

   这将在窗口中打开字符串表。

1. 选择字符串表末尾的空白行，键入字符串的文本或标题：例如，"其他属性页"。

   这将打开显示标题和**ID**框**的****字符串属性**页面。 **"标题"** 框包含您键入的字符串。

1. 在**ID**框中，选择或键入字符串的 ID。 完成后按 Enter。

   此示例对新属性页的类型名称使用**IDS_SAMPLE_ADDPAGE。**

1. 使用**IDS_SAMPLE_ADDPPG_CAPTION**对 ID 和标题的"其他属性页"重复步骤 3 和 4。

1. 在。新属性页类的 CPP 文件（在此示例中）`CAddtlPropPage`修改，`CAddtlPropPage::CAddtlPropPageFactory::UpdateRegistry`以便 IDS_SAMPLE_ADDPAGE由[AfxOleRegisterPropertyPageClass](../mfc/reference/registering-ole-controls.md#afxoleregisterpropertypageclass)传递，如以下示例所示：

   [!code-cpp[NVC_MFC_AxUI#33](../mfc/codesnippet/cpp/mfc-activex-controls-adding-another-custom-property-page_2.cpp)]

1. 修改 的`CAddtlPropPage`构造函数，以便IDS_SAMPLE_ADDPPG_CAPTION传递给`COlePropertyPage`构造函数，如下所示：

   [!code-cpp[NVC_MFC_AxUI#34](../mfc/codesnippet/cpp/mfc-activex-controls-adding-another-custom-property-page_3.cpp)]

进行必要的修改后，将重建项目并使用测试容器来测试新的属性页。 请参阅 [使用测试容器测试属性和事件](../mfc/testing-properties-and-events-with-test-container.md) 了解有关如何访问测试容器的信息。

## <a name="see-also"></a>另请参阅

[MFC 活动X控制](../mfc/mfc-activex-controls.md)
