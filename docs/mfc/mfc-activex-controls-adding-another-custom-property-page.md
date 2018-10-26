---
title: MFC ActiveX 控件： 添加另一个自定义属性页 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- property pages [MFC], MFC ActiveX controls
- custom property pages [MFC]
- ActiveX controls [MFC], property pages
- MFC ActiveX controls [MFC], property pages
ms.assetid: fcf7e119-9f29-41a9-908d-e9b1607e08af
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1599500a775bcd1c76f2e63a1f7b20126a2fb329
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50078201"
---
# <a name="mfc-activex-controls-adding-another-custom-property-page"></a>MFC ActiveX 控件：添加另一自定义属性页

有时，ActiveX 控件将具有多个属性比正常可以容纳的一个属性页。 在这种情况下，可以将属性页添加到 ActiveX 控件以显示这些属性。

本文介绍将新的属性页添加到已具有至少一个属性页的 ActiveX 控件。 添加常用属性的详细信息页 （字体、 图片或颜色），请参阅文章[MFC ActiveX 控件： 使用常用属性页](../mfc/mfc-activex-controls-using-stock-property-pages.md)。

以下过程使用 ActiveX 控件向导创建的一个示例 ActiveX 控件框架。 因此，类名称和标识符是唯一的此示例。

使用 ActiveX 控件中的属性页面的详细信息，请参阅以下文章：

- [MFC ActiveX 控件：属性页](../mfc/mfc-activex-controls-property-pages.md)

- [MFC ActiveX 控件：使用常用属性页](../mfc/mfc-activex-controls-using-stock-property-pages.md)

    > [!NOTE]
    >  强烈建议页遵循标准的 ActiveX 控件属性页大小的新属性。 常用的图片和颜色属性页面度量值 250 x 62 对话框单元 (DLU)。 标准字体属性页是 250 x 110 Dlu。 ActiveX 控件向导创建的默认属性页使用 250 x 62 DLU 标准。

### <a name="to-insert-a-new-property-page-template-into-your-project"></a>若要向项目中插入新的属性页模板

1. 打开控件项目，在项目工作区中打开资源视图。

1. 右键单击在若要打开快捷菜单，然后单击资源视图**添加资源**。

1. 展开**对话框中**节点，然后选择**IDD_OLE_PROPPAGE_SMALL**。

1. 单击**新建**若要将资源添加到你的项目。

1. 选择要刷新属性窗口的新属性页面模板。

1. 输入一个新值**ID**属性。 此示例使用**IDD_PROPPAGE_NEWPAGE**。

1. 单击**保存**工具栏上。

### <a name="to-associate-the-new-template-with-a-class"></a>若要将新模板与类相关联

1. 打开类视图。

1. 右键单击要打开快捷菜单的类视图中。

1. 从快捷菜单中，单击**外**，然后单击**添加类**。

   这将打开[添加类](../ide/add-class-dialog-box.md)对话框。

1. 双击**MFC 类**模板。

1. 在中**类名**框中[MFC 类向导](../mfc/reference/mfc-add-class-wizard.md)，键入新的对话框类的名称。 (在此示例中， `CAddtlPropPage`。)

1. 如果你想要更改文件的名称，请单击**更改**。 键入你的实现和标头文件的名称或接受默认名称。

1. 在中**基类**框中，选择`COlePropertyPage`。

1. 在中**对话框 ID**框中，选择**IDD_PROPPAGE_NEWPAGE**。

9. 单击**完成**创建类。

若要允许控件的用户访问此新的属性页，请对控件的属性页 Id 宏部分 （位于控件实现文件） 进行以下更改：

[!code-cpp[NVC_MFC_AxUI#32](../mfc/codesnippet/cpp/mfc-activex-controls-adding-another-custom-property-page_1.cpp)]

请注意，您必须增加 BEGIN_PROPPAGEIDS 宏 （属性页计数） 从 1 到 2 的第二个参数。

您还必须修改控件实现文件 (。CPP) 文件以包括标头 (。H） 新的属性页类的文件。

下一步涉及创建两个新的字符串资源将为新的属性页中提供类型名称和标题。

#### <a name="to-add-new-string-resources-to-a-property-page"></a>若要将新字符串资源添加到属性页

1. 打开控件项目，打开资源视图。

1. 双击**字符串表**文件夹，然后再双击现有字符串表你想要添加字符串资源。

   这将在窗口中打开字符串表。

1. 选择在字符串表末尾的空白行并键入文本或标题的字符串： 例如，"其他属性页。"

   这将打开**字符串属性**页显示**标题**并**ID**框。 **标题**框包含您键入的字符串。

1. 在中**ID**框中，选择或输入的字符串 ID。 完成后，请按 Enter。

   此示例使用**IDS_SAMPLE_ADDPAGE**为新的属性页的类型名称。

1. 重复步骤 3 和 4 使用**IDS_SAMPLE_ADDPPG_CAPTION** ID 和"其他属性页"的标题。

1. 在。新的属性页类的 CPP 文件 (在此示例中， `CAddtlPropPage`) 修改`CAddtlPropPage::CAddtlPropPageFactory::UpdateRegistry`，以便通过传递 IDS_SAMPLE_ADDPAGE [AfxOleRegisterPropertyPageClass](../mfc/reference/registering-ole-controls.md#afxoleregisterpropertypageclass)，如下面的示例：

   [!code-cpp[NVC_MFC_AxUI#33](../mfc/codesnippet/cpp/mfc-activex-controls-adding-another-custom-property-page_2.cpp)]

1. 修改的构造函数`CAddtlPropPage`以便 IDS_SAMPLE_ADDPPG_CAPTION 传递到`COlePropertyPage`构造函数中的，按如下所示：

   [!code-cpp[NVC_MFC_AxUI#34](../mfc/codesnippet/cpp/mfc-activex-controls-adding-another-custom-property-page_3.cpp)]

之后进行必要的修改后重新生成项目并使用测试容器测试新的属性页。 请参阅 [使用测试容器测试属性和事件](../mfc/testing-properties-and-events-with-test-container.md) 了解有关如何访问测试容器的信息。

## <a name="see-also"></a>请参阅

[MFC ActiveX 控件](../mfc/mfc-activex-controls.md)

