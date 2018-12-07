---
title: 演练：更新 MFC 随意画图应用程序（第 2 部分）
ms.date: 09/20/2018
helpviewer_keywords:
- walkthroughs [MFC]
ms.assetid: 602df5c2-17d4-4cd9-8cf6-dff652c4cae5
ms.openlocfilehash: 6a52486658307f001001e91772dad1167730def2
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/10/2018
ms.locfileid: "51519264"
---
# <a name="walkthrough-updating-the-mfc-scribble-application-part-2"></a>演练：更新 MFC 随意画图应用程序（第 2 部分）

[第 1 部分](../mfc/walkthrough-updating-the-mfc-scribble-application-part-1.md)本演练介绍了如何将 Office Fluent 功能区添加到经典的自由曲线应用程序。 此部分演示如何添加功能区面板和控件，用户可以使用而不是菜单和命令。

## <a name="prerequisites"></a>系统必备

[Visual C++ 示例](../visual-cpp-samples.md)

##  <a name="top"></a> 部分

本演练的此部分包含以下部分：

- [将新面板添加到功能区](#addnewpanel)

- [将帮助面板添加到功能区](#addhelppanel)

- [将笔面板添加到功能区](#addpenpanel)

- [添加到功能区颜色按钮](#addcolorbutton)

- [将颜色成员添加到文档类](#addcolormember)

- [初始化笔和保存首选项](#initpensave)

##  <a name="addnewpanel"></a> 将新面板添加到功能区

以下步骤演示如何添加**视图**面板，其中包含两个复选框控制的工具栏和状态栏，可见性以及**窗口**包含垂直方向的拆分面板按钮，用于控制创建和排列方式的多文档界面 (MDI) 窗口。

### <a name="to-add-a-view-panel-and-window-panel-to-the-ribbon-bar"></a>若要将视图面板和窗口面板添加到功能区栏

1. 创建名为一个面板`View`，其中包含两个复选框的切换状态栏和工具栏。

   1. 从**工具箱**，拖动**面板**到**主页**类别。 然后将两个**复选框**到面板。

   1. 单击要修改其属性的面板。 更改**标题**到`View`。

   1. 单击第一个的复选框，来修改其属性。 更改**ID**到`ID_VIEW_TOOLBAR`并**标题**到`Toolbar`。

   1. 单击第二个的复选框，来修改其属性。 更改**ID**到`ID_VIEW_STATUS_BAR`并**标题**到`Status Bar`。

1. 创建名为一个面板`Window`具有拆分按钮。 当用户单击拆分按钮时，快捷菜单将显示已在随意画图应用程序中定义的三个命令。

   1. 从**工具箱**，拖动**面板**到**主页**类别。 然后将拖**按钮**到面板。

   1. 单击要修改其属性的面板。 更改**标题**到`Window`。

   1. 单击按钮。 更改**标题**到`Windows`，**密钥**到`w`，**大图像索引**到`1`，并**拆分模式**到`False`。 然后单击省略号 (**...**) 旁边**菜单项**以打开**项编辑器**对话框。

   1. 单击**添加**三次以添加三个按钮。

   1. 单击第一个按钮，然后更改**标题**到`New Window`，和**ID**到`ID_WINDOW_NEW`。

   1. 单击第二个按钮，然后更改**标题**到`Cascade`，和**ID**到`ID_WINDOW_CASCADE`。

   1. 单击第三个按钮，然后更改**标题**到`Tile`，和**ID**到`ID_WINDOW_TILE_HORZ`。

1. 保存所做的更改，然后生成并运行应用程序。 **视图**并**窗口**应显示面板。 单击按钮来确认它们正常运行。

##  <a name="addhelppanel"></a> 将帮助面板添加到功能区

现在，将分配到功能区按钮名为随意画图应用程序中定义的两个菜单项**帮助主题**并**有关 Scribble**。 这些按钮将添加到名为的新面板**帮助**。

### <a name="to-add-a-help-panel"></a>若要添加的帮助面板

1. 从**工具箱**，拖动**面板**到**主页**类别。 然后将两个**按钮**到面板。

1. 单击要修改其属性的面板。 更改**标题**到`Help`。

1. 单击第一个按钮。 更改**标题**到`Help Topics`，和**ID**到`ID_HELP_FINDER`。

1. 单击第二个按钮。 更改**标题**到`About Scribble...`，和**ID**到`ID_APP_ABOUT`。

1. 保存所做的更改，然后生成并运行应用程序。 一个**帮助**应显示面板，其中包含两个功能区按钮。

   > [!IMPORTANT]
   > 当您单击**帮助主题**按钮，随意画图应用程序会打开名为的压缩 (.chm) HTML 帮助文件*your_project_name*。 chm。 因此，如果你的项目不是随意画图，您必须重的帮助文件命名为你的项目名称。

##  <a name="addpenpanel"></a> 将笔面板添加到功能区

现在，添加一个面板，以显示控制粗细和笔的颜色按钮。 此面板包含一个复选框，粗线和细笔之间切换。 其功能类似于**粗线**随意画图应用程序中的菜单项。

原始随意画图应用程序使用户可以从一个对话框将显示在用户单击时，选择笔宽度**笔宽度**菜单上。 由于功能区栏有充足的空间，为新控件，可以通过使用功能区上的两个组合框来替换对话框的。 一个组合框调整细笔的宽度和其他组合框调整粗笔的宽度。

#### <a name="to-add-a-pen-panel-and-combo-boxes-to-the-ribbon"></a>若要将笔面板和组合框添加到功能区

1. 从**工具箱**，拖动**面板**到**主页**类别。 然后将拖**复选框**并将两个**组合框**到面板。

1. 单击要修改其属性的面板。 更改**标题**到`Pen`。

1. 单击复选框。 更改**标题**到`Use Thick`，和**ID**到`ID_PEN_THICK_OR_THIN`。

1. 单击第一个组合框。 更改**标题**到`Thin Pen`， **ID**到`ID_PEN_THIN_WIDTH`，**类型**到`Drop List`，**数据**到`1;2;3;4;5;6;7;8;9;`，并**文本**到`2`。

1. 单击第二个的组合框。 更改**标题**到`Thick Pen`， **ID**到`ID_PEN_THICK_WIDTH`，**类型**到`Drop List`，**数据**到`5;6;7;8;9;10;11;12;13;14;15;16;17;18;19;20;`，并**文本**到`5`。

1. 新的组合框不对应任何现有的菜单项，因此必须创建每笔选项的菜单项。

   1. 在中**资源视图**窗口中，打开**IDR_SCRIBBTYPE**菜单资源。

   1. 单击**笔**以打开钢笔菜单。 然后单击**请在此处输入**并键入`Thi&n Pen`。

   1. 右键单击刚才打开的文本**属性**窗口，然后更改 ID 属性设置为`ID_PEN_THIN_WIDTH`。

   1. 创建每个笔菜单项的事件处理程序。 右键单击**此应用程序 & n 笔**菜单项，您创建，然后单击**添加事件处理程序**。 **事件处理程序向导**显示。

   1. 在中**类列表**框中的向导中，选择**CScribbleDoc** ，然后单击**添加和编辑**。 该命令创建名为一个事件处理程序`CScribbleDoc::OnPenThinWidth`。

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

1. 接下来，创建一个菜单项和事件处理程序粗笔。

   1. 在中**资源视图**窗口中，打开**IDR_SCRIBBTYPE**菜单资源。

   1. 单击**笔**以打开钢笔菜单。 然后单击**请在此处输入**并键入`Thic&k Pen`。

   1. 右键单击您键入要显示的文本**属性**窗口。 将 ID 属性更改为`ID_PEN_THICK_WIDTH`。

   1. 右键单击**胖笔**菜单项，您创建，然后单击**添加事件处理程序**。 **事件处理程序向导**显示。

   1. 在中**类列表**框中的向导中，选择**CScribbleDoc** ，然后单击**添加和编辑**。 该命令创建名为一个事件处理程序`CScribbleDoc::OnPenThickWidth`。

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

1. 保存所做的更改，然后生成并运行应用程序。 应显示新的按钮和组合框。 请尝试使用其他笔宽度 scribble。

##  <a name="addcolorbutton"></a> 将颜色按钮添加到笔面板

接下来，添加[CMFCRibbonColorButton](../mfc/reference/cmfcribboncolorbutton-class.md)对象，使用户能够自由曲线的颜色。

### <a name="to-add-a-color-button-to-the-pen-panel"></a>若要将颜色按钮添加到笔面板

1. 添加颜色按钮之前，请为其创建菜单项。 在中**资源视图**窗口中，打开**IDR_SCRIBBTYPE**菜单资源。 单击**笔**菜单项以打开钢笔菜单。 然后单击**请在此处输入**并键入`&Color`。 右键单击您键入要显示的文本**属性**窗口。 将 ID 更改为 `ID_PEN_COLOR`。

1. 现在，添加颜色按钮。 从**工具箱**，拖动**颜色按钮**到**笔**面板。

1. 单击颜色按钮。 更改**标题**到`Color`， **ID**到`ID_PEN_COLOR`，**简单介绍**到`True`，**大图像索引**到`1`，并**拆分模式**到`False`。

1. 保存所做的更改，然后生成并运行应用程序。 新的颜色按钮应显示在**笔**面板。 但是，它不能使用因为它尚不具有事件处理程序。 后续步骤演示如何添加颜色按钮的事件处理程序。

##  <a name="addcolormember"></a> 将颜色成员添加到文档类

由于原始随意画图应用程序没有颜色的笔，则必须为其编写实现。 若要存储的文档，笔颜色将新成员添加到文档类， `CscribbleDoc`。

### <a name="to-add-a-color-member-to-the-document-class"></a>若要将颜色成员添加到文档类

1. 在 scribdoc.h，在`CScribbleDoc`类中，找到`// Attributes`部分。 将以下代码行添加后的定义`m_nThickWidth`数据成员。

   ```cpp
   // Current pen color
   COLORREF m_penColor;
   ```

1. 每个文档包含一系列笔尖用户已绘制。 通过定义每个笔画`CStroke`对象。 `CStroke`类不包括有关钢笔颜色的信息，因此必须修改类。 在 scribdoc.h，在`CStroke`类中，添加以下代码行后的定义`m_nPenWidth`数据成员。

   ```cpp
   // Pen color for the stroke
   COLORREF m_penColor;
   ```

1. 在 scribdoc.h，添加一个新`CStroke`构造函数的参数指定宽度和颜色。 添加以下行后的代码`CStroke(UINT nPenWidth);`语句。

   ```cpp
   CStroke(UINT nPenWidth, COLORREF penColor);
   ```

1. 在 scribdoc.cpp，添加新的实现`CStroke`构造函数。 将以下代码添加的实施后`CStroke::CStroke(UINT nPenWidth)`构造函数。

   ```cpp
   // Constructor that uses the document's current width and color
   CStroke::CStroke(UINT nPenWidth, COLORREF penColor)
   {
       m_nPenWidth = nPenWidth;
       m_penColor = penColor;
       m_rectBounding.SetRectEmpty();
   }
   ```

1. 更改的第二行`CStroke::DrawStroke`方法，如下所示。

   ```cpp
   if (!penStroke.CreatePen(PS_SOLID, m_nPenWidth, m_penColor))
   ```

1. 设置文档类的默认笔颜色。 在 scribdoc.cpp，添加以下行`CScribbleDoc::InitDocument`后，`m_nThickWidth = 5;`语句。

   ```cpp
   // default pen color is black
   m_penColor = RGB(0, 0, 0);
   ```

1. 在 scribdoc.cpp，更改的第一行`CScribbleDoc::NewStroke`所示的方法。

   ```cpp
   CStroke* pStrokeItem = new CStroke(m_nPenWidth, m_penColor);
   ```

1. 更改的最后一行`CScribbleDoc::ReplacePen`所示的方法。

   ```cpp
   m_penCur.CreatePen(PS_SOLID, m_nPenWidth, m_penColor);
   ```

1. 您添加`m_penColor`上一步中的成员。 现在，创建的事件处理程序设置的成员的颜色按钮。

   1. 在中**资源视图**窗口中，打开 IDR_SCRIBBTYPE 菜单资源。

   1. 右键单击**颜色**菜单项，并单击**添加事件处理程序**。 **事件处理程序向导**出现。

   1. 在中**类列表**框中的向导中，选择**CScribbleDoc** ，然后单击**添加和编辑**按钮。 该命令将创建`CScribbleDoc::OnPenColor`事件处理程序存根 （stub)。

1. 替换为存根`CScribbleDoc::OnPenColor`事件处理程序替换下面的代码。

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

1. 保存所做的更改，然后生成并运行应用程序。 现在可以按颜色按钮，并更改笔的颜色。

##  <a name="initpensave"></a> 初始化笔和保存首选项

接下来，初始化颜色和笔的宽度。 最后，保存并加载了颜色绘图从文件。

### <a name="to-initialize-controls-on-the-ribbon-bar"></a>若要初始化的功能区栏上的控件

1. 在功能区栏上的手写笔进行初始化。

   在将以下代码添加到 scribdoc.cpp，`CScribbleDoc::InitDocument`方法后，`m_sizeDoc = CSize(200,200)`语句。

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

1. 保存到文件中绘制的颜色。 在中添加到 scribdoc.cpp，下面的语句`CStroke::Serialize`方法后，`ar << (WORD)m_nPenWidth;`语句。

   ```cpp
   ar << (COLORREF)m_penColor;
   ```

1. 最后，加载了颜色绘图从文件。 在中添加以下代码，行`CStroke::Serialize`方法后，`m_nPenWidth = w;`语句。

   ```cpp
   ar >> m_penColor;
   ```

1. 现在 scribble 颜色，并将绘图保存到一个文件。

## <a name="conclusion"></a>结束语

已更新 MFC 随意画图应用程序。 修改现有的应用程序时，本演练使用作为指南。

## <a name="see-also"></a>请参阅

[演练](../mfc/walkthroughs-mfc.md)<br/>
[演练：更新 MFC 随意画图应用程序（第 1 部分）](../mfc/walkthrough-updating-the-mfc-scribble-application-part-1.md)
