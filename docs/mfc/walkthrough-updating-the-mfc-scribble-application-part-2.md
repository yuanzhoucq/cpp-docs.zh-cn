---
title: 演练：更新 MFC 随意画图应用程序（第 2 部分）
ms.date: 04/25/2019
helpviewer_keywords:
- walkthroughs [MFC]
ms.assetid: 602df5c2-17d4-4cd9-8cf6-dff652c4cae5
ms.openlocfilehash: bc204a152168accf3731eede8ca9ef960ab121d2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360232"
---
# <a name="walkthrough-updating-the-mfc-scribble-application-part-2"></a>演练：更新 MFC 随意画图应用程序（第 2 部分）

本演练[的第 1 部分](../mfc/walkthrough-updating-the-mfc-scribble-application-part-1.md)演示如何向经典 Scribble 应用程序添加 Office Fluent 功能区。 本部分演示如何添加功能区面板和控件，用户可以使用这些面板和控件，而不是菜单和命令。

## <a name="prerequisites"></a>先决条件

[Visual C++ 示例](../overview/visual-cpp-samples.md)

## <a name="sections"></a><a name="top"></a>部分

本演练的这一部分有以下部分：

- [向功能区添加新面板](#addnewpanel)

- [向功能区添加帮助面板](#addhelppanel)

- [将笔面板添加到功能区](#addpenpanel)

- [向功能区添加颜色按钮](#addcolorbutton)

- [向文档类添加颜色成员](#addcolormember)

- [初始化笔和保存首选项](#initpensave)

## <a name="adding-new-panels-to-the-ribbon"></a><a name="addnewpanel"></a>向功能区添加新面板

这些步骤演示如何添加**一个视图**面板，其中包含两个控制工具栏和状态栏可见性的复选框，**以及包含垂直**方向拆分按钮的窗口面板，该按钮控制多文档接口 （MDI） 窗口的创建和排列。

### <a name="to-add-a-view-panel-and-window-panel-to-the-ribbon-bar"></a>将"视图"面板和"窗口"面板添加到功能区栏

1. 创建名为 的`View`面板，其中有两个复选框来切换状态栏和工具栏。

   1. 从 **"工具箱**"，将**面板**拖动到 **"主页"** 类别。 然后，将两**个复选框**拖动到面板。

   1. 单击面板可修改其属性。 将**标题**更改为`View`。

   1. 单击第一个复选框以修改其属性。 将**ID**ID`ID_VIEW_TOOLBAR`更改为`Toolbar`和**标题**。

   1. 单击第二个复选框以修改其属性。 将**ID**ID`ID_VIEW_STATUS_BAR`更改为`Status Bar`和**标题**。

1. 创建具有拆分按钮`Window`的名为的面板。 当用户单击拆分按钮时，快捷菜单将显示三个已在 Scribble 应用程序中定义的命令。

   1. 从 **"工具箱**"，将**面板**拖动到 **"主页"** 类别。 然后，将**按钮**拖动到面板。

   1. 单击面板可修改其属性。 将**标题**更改为`Window`。

   1. 单击按钮。 将**标题**更改为`Windows` **Keys** ，键`w`更改为 ，**将大图像索引**更改为`1`，`False`并将**模式拆分为**。 然后单击**菜单项**旁边的省略号 （**...）** 以打开 **"项目编辑器"** 对话框。

   1. 单击 **"添加**三次"可添加三个按钮。

   1. 单击第一个按钮，然后将 **"标题"** 更改为`New Window`"，ID 更改为**ID**`ID_WINDOW_NEW`。

   1. 单击第二个按钮，然后将 **"标题"**`Cascade`更改为**ID** `ID_WINDOW_CASCADE`"ID"，并将"标题"更改为 。

   1. 单击第三个按钮，然后将 **"标题"** 更改为`Tile`"，**并将 ID**更改为`ID_WINDOW_TILE_HORZ`。

1. 保存更改，然后生成并运行应用程序。 应显示 **"视图**"和"**窗口**"面板。 单击按钮以确认它们正常工作。

## <a name="adding-a-help-panel-to-the-ribbon"></a><a name="addhelppanel"></a>向功能区添加帮助面板

现在，您可以将在 Scribble 应用程序中定义的两个菜单项分配给名为"**帮助主题**"和"**关于涂鸦"的**功能区按钮。 这些按钮将添加到名为 **"帮助**"的新面板中。

### <a name="to-add-a-help-panel"></a>添加帮助面板

1. 从 **"工具箱**"，将**面板**拖动到 **"主页"** 类别。 然后，将两**个按钮**拖动到面板上。

1. 单击面板可修改其属性。 将**标题**更改为`Help`。

1. 单击第一个按钮。 将**标题**更改为`Help Topics`，**ID**并将`ID_HELP_FINDER`ID 更改为 。

1. 单击第二个按钮。 将**标题**更改为`About Scribble...`，**ID**并将`ID_APP_ABOUT`ID 更改为 。

1. 保存更改，然后生成并运行应用程序。 应显示包含两个功能区按钮**的帮助**面板。

   > [!IMPORTANT]
   > 单击"**帮助主题"** 按钮时，Scribble 应用程序将打开名为*your_project_name*.chm 的压缩 HTML （.chm） 帮助文件。 因此，如果项目未命名为 Scribble，则必须将帮助文件重命名为项目名称。

## <a name="adding-a-pen-panel-to-the-ribbon"></a><a name="addpenpanel"></a>将笔面板添加到功能区

现在，添加一个面板来显示控制笔的厚度和颜色的按钮。 此面板包含一个在粗笔和细笔之间切换的复选框。 其功能类似于 Scribble 应用程序中的 **"厚线**"菜单项。

原始涂鸦应用程序允许用户从对话框中选择笔宽度，当用户单击菜单上的 **"笔宽度**"时显示。 由于功能区栏有足够的空间用于新控件，因此可以使用功能区上的两个组合框替换对话框。 一个组合框调整细笔的宽度，另一个组合框调整粗笔的宽度。

#### <a name="to-add-a-pen-panel-and-combo-boxes-to-the-ribbon"></a>将"笔"面板和组合框添加到功能区

1. 从 **"工具箱**"，将**面板**拖动到 **"主页"** 类别。 然后，将**复选框**和两个**组合框**拖动到面板中。

1. 单击面板可修改其属性。 将**标题**更改为`Pen`。

1. 单击此复选框。 将**标题**更改为`Use Thick`，**ID**并将`ID_PEN_THICK_OR_THIN`ID 更改为 。

1. 单击第一个组合框。 将**标题**更改为`Thin Pen` **，ID**更改为`ID_PEN_THIN_WIDTH` `Drop List`，**键入**`1;2;3;4;5;6;7;8;9;`到 ，**数据**更改为 ， 并将**文本**更改为`2`。

1. 单击第二个组合框。 将**标题**更改为`Thick Pen` **，ID**更改为`ID_PEN_THICK_WIDTH` `Drop List`，**键入**`5;6;7;8;9;10;11;12;13;14;15;16;17;18;19;20;`到 ，**数据**更改为 ， 并将**文本**更改为`5`。

1. 新的组合框不对应于任何现有的菜单项，因此您必须为每个笔选项创建一个菜单项。

   1. 在 **"资源视图"** 窗口中，打开**IDR_SCRIBBTYPE**菜单资源。

   1. 单击 **"笔"** 可打开笔菜单。 然后单击 **"在此处键入"** 并`Thi&n Pen`键入 。

   1. 右键单击键入的文本以打开 **"属性"** 窗口，然后将 ID 属性更改为`ID_PEN_THIN_WIDTH`。

   1. 为每个笔菜单项创建事件处理程序。 右键单击您创建的**Th&n 笔**菜单项，然后单击"**添加事件处理程序**"。 将显示**事件处理程序向导**。

   1. 在向导中的 **"类"列表**框中，选择**CScribbleDoc，** 然后单击"**添加和编辑**"。 该命令创建名为 的事件处理程序`CScribbleDoc::OnPenThinWidth`。

   1. 将下列代码添加到 `CScribbleDoc::OnPenThinWidth`。

        ```cpp
        // Get a pointer to the ribbon bar
        CMFCRibbonBar* pRibbon = ((CMDIFrameWndEx*) AfxGetMainWnd())->GetRibbonBar();
        ASSERT_VALID(pRibbon);

        // Get a pointer to the Thin Width combo box
        CMFCRibbonComboBox* pThinComboBox = DYNAMIC_DOWNCAST(
        CMFCRibbonComboBox, pRibbon->FindByID(ID_PEN_THIN_WIDTH));

        //Get the selected value
        int nCurSel = pThinComboBox->GetCurSel();
        if (nCurSel>= 0)
        {
            m_nThinWidth = atoi(CStringA(pThinComboBox->GetItem(nCurSel)));
        }

        // Create a new pen using the selected width
        ReplacePen();
        ```

1. 接下来，为粗笔创建菜单项和事件处理程序。

   1. 在 **"资源视图"** 窗口中，打开**IDR_SCRIBBTYPE**菜单资源。

   1. 单击 **"笔"** 可打开笔菜单。 然后单击 **"在此处键入"** 并`Thic&k Pen`键入 。

   1. 右键单击键入的文本以显示 **"属性"** 窗口。 将 ID 属性`ID_PEN_THICK_WIDTH`更改为 。

   1. 右键单击您创建的 **"厚笔"** 菜单项，然后单击"**添加事件处理程序**"。 将显示**事件处理程序向导**。

   1. 在向导的 **"类"列表**框中，选择**CScribbleDoc，** 然后单击"**添加和编辑**"。 该命令创建名为 的事件处理程序`CScribbleDoc::OnPenThickWidth`。

   1. 将下列代码添加到 `CScribbleDoc::OnPenThickWidth`。

        ```cpp
        // Get a pointer to the ribbon bar
        CMFCRibbonBar* pRibbon = ((CMDIFrameWndEx *) AfxGetMainWnd())->GetRibbonBar();
        ASSERT_VALID(pRibbon);

        CMFCRibbonComboBox* pThickComboBox = DYNAMIC_DOWNCAST(
            CMFCRibbonComboBox, pRibbon->FindByID(ID_PEN_THICK_WIDTH));
        // Get the selected value
        int nCurSel = pThickComboBox->GetCurSel();
        if (nCurSel>= 0)
        {
            m_nThickWidth = atoi(CStringA(pThickComboBox->GetItem(nCurSel)));
        }

        // Create a new pen using the selected width
        ReplacePen();
        ```

1. 保存更改，然后生成并运行应用程序。 应显示新的按钮和组合框。 尝试使用不同的笔宽进行涂鸦。

## <a name="adding-a-color-button-to-the-pen-panel"></a><a name="addcolorbutton"></a>向笔面板添加颜色按钮

接下来，添加一个[CMFCRibbonColorButton](../mfc/reference/cmfcribboncolorbutton-class.md)对象，允许用户以颜色涂鸦。

### <a name="to-add-a-color-button-to-the-pen-panel"></a>向"笔"面板添加颜色按钮

1. 在添加颜色按钮之前，请为其创建菜单项。 在 **"资源视图"** 窗口中，打开**IDR_SCRIBBTYPE**菜单资源。 单击 **"笔"** 菜单项以打开笔菜单。 然后单击 **"在此处键入"** 并`&Color`键入 。 右键单击键入的文本以显示 **"属性"** 窗口。 将 ID 更改为 `ID_PEN_COLOR`。

1. 现在添加颜色按钮。 从 **"工具箱**"，将 **"颜色按钮**"拖动到 **"笔"** 面板。

1. 单击颜色按钮。 将**标题**更改为`Color` **，ID** `ID_PEN_COLOR`更改为 "`True`**简单查找**"，**将大图像索引**更改为`1`，将 **"拆分模式"** 更改为`False`。

1. 保存更改，然后生成并运行应用程序。 新的颜色按钮应显示在 **"笔"** 面板上。 但是，它不能使用它，因为它还没有一个事件处理程序。 接下来的步骤演示如何为颜色按钮添加事件处理程序。

## <a name="adding-a-color-member-to-the-document-class"></a><a name="addcolormember"></a>向文档类添加颜色成员

由于原始 Scribble 应用程序没有彩色笔，因此必须为其编写实现。 要存储文档的笔颜色，向文档类添加新成员`CscribbleDoc`。

### <a name="to-add-a-color-member-to-the-document-class"></a>向文档类添加颜色成员

1. 在 scribdoc.h 中`CScribbleDoc`，在班级中`// Attributes`，找到该部分。 在`m_nThickWidth`定义数据成员后添加以下代码行。

   ```cpp
   // Current pen color
   COLORREF m_penColor;
   ```

1. 每个文档都包含用户已绘制的引点列表。 每个描边都由`CStroke`对象定义。 类`CStroke`不包括有关笔颜色的信息，因此必须修改类。 在 scribdoc.h 中`CStroke`，在类中，在`m_nPenWidth`数据成员定义之后添加以下代码行。

   ```cpp
   // Pen color for the stroke
   COLORREF m_penColor;
   ```

1. 在 scribdoc.h 中，`CStroke`添加一个新构造函数，其参数指定宽度和颜色。 在`CStroke(UINT nPenWidth);`语句之后添加以下代码行。

   ```cpp
   CStroke(UINT nPenWidth, COLORREF penColor);
   ```

1. 在 scribdoc.cpp 中，添加新`CStroke`构造函数的实现。 在`CStroke::CStroke(UINT nPenWidth)`构造函数实现后添加以下代码。

   ```cpp
   // Constructor that uses the document's current width and color
   CStroke::CStroke(UINT nPenWidth, COLORREF penColor)
   {
       m_nPenWidth = nPenWidth;
       m_penColor = penColor;
       m_rectBounding.SetRectEmpty();
   }
   ```

1. 更改`CStroke::DrawStroke`方法的第二行，如下所示。

   ```cpp
   if (!penStroke.CreatePen(PS_SOLID, m_nPenWidth, m_penColor))
   ```

1. 设置文档类的默认笔颜色。 在 scribdoc.cpp 中，在`CScribbleDoc::InitDocument``m_nThickWidth = 5;`语句之后向 添加以下行。

   ```cpp
   // default pen color is black
   m_penColor = RGB(0, 0, 0);
   ```

1. 在 scribdoc.cpp 中，将`CScribbleDoc::NewStroke`方法的第一行更改为以下内容。

   ```cpp
   CStroke* pStrokeItem = new CStroke(m_nPenWidth, m_penColor);
   ```

1. 将方法的最后一`CScribbleDoc::ReplacePen`行更改为以下内容。

   ```cpp
   m_penCur.CreatePen(PS_SOLID, m_nPenWidth, m_penColor);
   ```

1. 您在上`m_penColor`一步中添加了该成员。 现在，为设置成员的颜色按钮创建事件处理程序。

   1. 在 **"资源视图"** 窗口中，打开IDR_SCRIBBTYPE菜单资源。

   1. 右键单击 **"颜色"** 菜单项，然后单击"**添加事件处理程序**"。 将显示**事件处理程序向导**。

   1. 在向导中的 **"类"列表**框中，选择**CScribbleDoc，** 然后单击"**添加和编辑**"按钮。 该命令创建`CScribbleDoc::OnPenColor`事件处理程序存根。

1. 将事件处理程序的`CScribbleDoc::OnPenColor`存根替换为以下代码。

   ```cpp
   void CScribbleDoc::OnPenColor()
   {
       // Change pen color to reflect color button's current selection
       CMFCRibbonBar* pRibbon = ((CMDIFrameWndEx*) AfxGetMainWnd())->GetRibbonBar();
       ASSERT_VALID(pRibbon);

       CMFCRibbonColorButton* pColorBtn = DYNAMIC_DOWNCAST(
           CMFCRibbonColorButton, pRibbon->FindByID(ID_PEN_COLOR));

       m_penColor = pColorBtn->GetColor();
       // Create new pen using the selected color
       ReplacePen();
   }
   ```

1. 保存更改，然后生成并运行应用程序。 现在，您可以按颜色按钮并更改笔的颜色。

## <a name="initializing-pens-and-saving-preferences"></a><a name="initpensave"></a>初始化笔和保存首选项

接下来，初始化笔的颜色和宽度。 最后，从文件保存并加载彩色图形。

### <a name="to-initialize-controls-on-the-ribbon-bar"></a>在功能区栏上初始化控件

1. 初始化功能区栏上的笔。

   在`CScribbleDoc::InitDocument``m_sizeDoc = CSize(200,200)`语句之后的方法中将以下代码添加到 scribdoc.cpp 中。

   ```cpp
   // Reset the ribbon UI to its initial values
   CMFCRibbonBar* pRibbon =
       ((CMDIFrameWndEx*) AfxGetMainWnd())->GetRibbonBar();
   ASSERT_VALID(pRibbon);

   CMFCRibbonColorButton* pColorBtn = DYNAMIC_DOWNCAST(
       CMFCRibbonColorButton,
       pRibbon->FindByID(ID_PEN_COLOR));

   // Set ColorButton to black
   pColorBtn->SetColor(RGB(0, 0, 0));

   CMFCRibbonComboBox* pThinComboBox = DYNAMIC_DOWNCAST(
       CMFCRibbonComboBox,
       pRibbon->FindByID(ID_PEN_THIN_WIDTH));

   // Set Thin pen combobox to 2
   pThinComboBox->SelectItem(1);

   CMFCRibbonComboBox* pThickComboBox = DYNAMIC_DOWNCAST(
       CMFCRibbonComboBox,
       pRibbon->FindByID(ID_PEN_THICK_WIDTH));

   // Set Thick pen combobox to 5
   pThickComboBox->SelectItem(0);
   ```

1. 将彩色图形保存到文件中。 在`CStroke::Serialize``ar << (WORD)m_nPenWidth;`语句之后的方法中将以下语句添加到 scribdoc.cpp。

   ```cpp
   ar << (COLORREF)m_penColor;
   ```

1. 最后，从文件加载彩色图形。 在`CStroke::Serialize``m_nPenWidth = w;`语句之后的方法中添加以下代码行。

   ```cpp
   ar >> m_penColor;
   ```

1. 现在，以彩色涂鸦，并将绘图保存到文件中。

## <a name="conclusion"></a>结束语

您已更新 MFC 涂鸦应用程序。 修改现有应用程序时，请本演练作为指南。

## <a name="see-also"></a>另请参阅

[演练](../mfc/walkthroughs-mfc.md)<br/>
[演练：更新 MFC 随意画图应用程序（第 1 部分）](../mfc/walkthrough-updating-the-mfc-scribble-application-part-1.md)
