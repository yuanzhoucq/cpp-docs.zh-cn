---
title: "MFC ActiveX 控件：添加另一自定义属性页 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ActiveX 控件 [C++], 属性页"
  - "自定义属性页"
  - "MFC ActiveX 控件 [C++], 属性页"
  - "属性页 [C++], MFC ActiveX 控件"
ms.assetid: fcf7e119-9f29-41a9-908d-e9b1607e08af
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MFC ActiveX 控件：添加另一自定义属性页
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

偶尔，ActiveX 控件比在一个属性页会有更多属性可以合理的。  在这种情况下，您可以将属性添加页到 ActiveX 控件显示这些属性。  
  
 已至少有一个属性页的本文讨论添加新的属性页。ActiveX 控件。  有关添加常用属性页的更多信息 \(字体、图片或颜色\)，请参见 [MFC ActiveX 控件：使用常用属性页](../mfc/mfc-activex-controls-using-stock-property-pages.md)文章。  
  
 以下过程使用 ActiveX 控件向导"创建 ActiveX 的示例控件框架。  因此，类名和标识符。此示例是唯一的。  
  
 有关使用属性页的更多信息，请参见下列文章：在 ActiveX 控件  
  
-   [MFC ActiveX 控件：属性页](../mfc/mfc-activex-controls-property-pages.md)  
  
-   [MFC ActiveX 控件：使用常用属性页](../mfc/mfc-activex-controls-using-stock-property-pages.md)  
  
    > [!NOTE]
    >  强烈建议新的页属性遵循 ActiveX 控件属性页的范围标准。  将图片和颜色属性页对话框 250x62 度量单位 \(控件\)。  标准字体属性页是 250x110 DLU。  ActiveX 控件向导创建的默认属性页使用 250x62 DLU 标准。  
  
### 插入新的"属性页模板到项目  
  
1.  打开控件的项目，则在项目工作区中打开资源视图。  
  
2.  右击在"资源视图打开快捷菜单并单击 **添加资源**。  
  
3.  展开 **对话框** 节点，然后选择 **IDD\_OLE\_PROPPAGE\_SMALL**。  
  
4.  单击 `New` 将资源添加到此项目。  
  
5.  选择新的属性页刷新模板属性窗口。  
  
6.  输入 **ID** 属性的新值。  此示例使用 **IDD\_PROPPAGE\_NEWPAGE**。  
  
7.  在工具栏上单击**“保存”**。  
  
### 相关新的模板类。  
  
1.  打开类视图。  
  
2.  右击类视图打开快捷菜单。  
  
3.  从快捷菜单中单击“添加”，然后单击“添加类”。  
  
     这会打开 [添加类](../ide/add-class-dialog-box.md) 对话框。  
  
4.  双击 **MFC 类** 模板。  
  
5.  在 **类名** 框在 [MFC 类向导](../mfc/reference/mfc-add-class-wizard.md)中，键入项目名称。新的对话框类。\(在此示例中，即 `CAddtlPropPage`。\)  
  
6.  如果要更改文件的名称，单击 **更改**。  输入名称。实现和头文件或接受默认名称。  
  
7.  在 **基类** 框中，选择 `COlePropertyPage`。  
  
8.  在 **对话框 ID** 框中，选择 **IDD\_PROPPAGE\_NEWPAGE**。  
  
9. 单击以创建类的 **完成** 。  
  
 若要允许设置为此新的属性页中的用户控件访问，请对控件的 ID 属性页的节进行以下更改 \(位于控件实现文件\):  
  
 [!code-cpp[NVC_MFC_AxUI#32](../mfc/codesnippet/CPP/mfc-activex-controls-adding-another-custom-property-page_1.cpp)]  
  
 注意必须增加 `BEGIN_PROPPAGEIDS` 宏 \(计数\) 属性页从 1 至 2. 中的第二个参数。  
  
 还必须修改控件实现文件 \(.cpp\) 中的文件标题 \(。H\) 新的属性页的类文件。  
  
 下一步是创建已为新的"属性页"将提供一类型名称和标题的两个字符串资源。  
  
#### 添加新的字符串资源。属性页  
  
1.  打开控件的项目，请打开资源视图。  
  
2.  双击 **字符串表** 文件夹然后双击要将字符串中现有的字符串表资源。  
  
     这将打开 Windows 中的字符串表。  
  
3.  选择空白行在字符串表结尾时键入文本、标题，字符串：例如，添加“附加属性页”。  
  
     这显示打开 **标题** 和 **ID** 对话框的 **String Properties** 页。  **标题** 框包含您键入的字符串。  
  
4.  在 **ID** 框中，选中或键入字符串的 ID。  完成后，按 Enter。  
  
     此示例适用于新的属性页的类型名使用 **IDS\_SAMPLE\_ADDPAGE**。  
  
5.  重复使用 **IDS\_SAMPLE\_ADDPPG\_CAPTION** 的步骤 3 和 4“ID 和其他属性页的”标题的。  
  
6.  在新的"属性页类的 .cpp 文件 \(在此示例中，`CAddtlPropPage`\) 修改 `CAddtlPropPage::CAddtlPropPageFactory::UpdateRegistry`，以便 IDS\_SAMPLE\_ADDPAGE 将 [AfxOleRegisterPropertyPageClass](../Topic/AfxOleRegisterPropertyPageClass.md)，如下面的示例所示：  
  
     [!code-cpp[NVC_MFC_AxUI#33](../mfc/codesnippet/CPP/mfc-activex-controls-adding-another-custom-property-page_2.cpp)]  
  
7.  如下修改 `CAddtlPropPage` 构造函数，以便 **IDS\_SAMPLE\_ADDPPG\_CAPTION** 传递给 `COlePropertyPage` 构造函数，例如：  
  
     [!code-cpp[NVC_MFC_AxUI#34](../mfc/codesnippet/CPP/mfc-activex-controls-adding-another-custom-property-page_3.cpp)]  
  
 在进行必要的更改重新生成项目并使用测试容器测试新的属性页。  有关如何访问测试容器的信息，请参见[用测试容器测试属性和事件](../mfc/testing-properties-and-events-with-test-container.md)。  
  
## 请参阅  
 [MFC ActiveX 控件](../mfc/mfc-activex-controls.md)