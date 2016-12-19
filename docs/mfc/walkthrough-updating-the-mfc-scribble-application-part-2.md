---
title: "演练：更新 MFC 随意画图应用程序（第 2 部分） | Microsoft Docs"
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
  - "演练 [C++]"
ms.assetid: 602df5c2-17d4-4cd9-8cf6-dff652c4cae5
caps.latest.revision: 36
caps.handback.revision: 32
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 演练：更新 MFC 随意画图应用程序（第 2 部分）
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在本演练的[Part 1](../mfc/walkthrough-updating-the-mfc-scribble-application-part-1.md)中，展示了如何添加Office Fluent 功能区到经典的Scribble应用程序  这部分演示如何添加用户可以使用代替菜单命令的和功能区面板和控件。  
  
## 系统必备  
 [Visual C\+\+ 示例](../top/visual-cpp-samples.md)  
  
##  <a name="top"></a> 各节内容  
 此演练部分包含以下部分：  
  
-   [将新功能区面板。](#addNewPanel)  
  
-   [将帮助添加到功能区面板](#addHelpPanel)  
  
-   [将钢笔添加到功能区面板](#addPenPanel)  
  
-   [向功能区中添加一个颜色按钮。](#addColorButton)  
  
-   [添加颜色文档成员添加到类](#addColorMember)  
  
-   [初始化钢笔和保存首选项](#initPenSave)  
  
##  <a name="addNewPanel"></a> 将新功能区面板。  
 以下步骤显示如何添加 **视图** 面板中控制工具栏和状态栏的可见性的两个复选框，然后垂直拆分按钮控件包含面向的多文档界面 \(MDI\) \(MDI\) 窗口中创建和排列方式的一 **窗口** 面板。  
  
#### 添加视图面板和面板功能区栏窗口。  
  
1.  创建一个名为 `视图`的面板，具有两个复选框切换状态栏和工具栏。  
  
    1.  从 **工具箱**中，将 **面板** 拖到 **主页** 类别。  然后拖动两到面板的 **复选框**。  
  
    2.  单击面板改变它的属性。  将**“标题”**更改为 `View`。  
  
    3.  单击第一个复选框修改其属性。  更改 **ID** 设置为 `ID_VIEW_TOOLBAR` 并将 **标题** 设置为 `工具栏`。  
  
    4.  单击第二个复选框修改其属性。  更改 **ID** 设置为 `ID_VIEW_STATUS_BAR` 并将 **标题** 设置为 `状态栏 (S)`。  
  
2.  创建具有拆分按钮和名为 `窗口` 的面板。  当用户单击按钮拆分，快捷菜单显示 Scribble 应用程序已定义的三个命令。  
  
    1.  从 **工具箱**中，将 **面板** 拖到 **主页** 类别。  然后将 **按钮** 拖到面板中。  
  
    2.  单击面板改变它的属性。  将**“标题”**更改为 `Window`。  
  
    3.  单击按钮。  **标题** 更改为 `窗口`，将 **键** 设置为 `w`，将 **索引大图像** 设置为 `1`并将 **拆分模式** 设置为 `False`。  然后单击 **菜单项** 旁边的省略号 \(**...**\) 打开 **项编辑器** 对话框。  
  
    4.  单击**“添加”**三次以添加三个按钮。  
  
    5.  单击第一个按钮将 **标题** 更改为 `新建窗口`并将 **ID** 设置为 `ID_WINDOW_NEW`。  
  
    6.  单击第二个按钮将 **标题** 更改为 `层叠`并将 **ID** 设置为 `ID_WINDOW_CASCADE`。  
  
    7.  单击第三个按钮将 **标题** 更改为 `平铺 (T)`并将 **ID** 设置为 `ID_WINDOW_TILE_HORZ`。  
  
3.  保存改变的，然后生成并运行应用程序。  应显示 **视图** 和 **窗口** 面板。  单击按钮提交这些工作正常。  
  
 \[[各节内容](#top)\]  
  
##  <a name="addHelpPanel"></a> 将帮助添加到功能区面板  
 现在，可以将该功能区按钮的 Scribble 应用程序中定义名为 **帮助主题** 和 **关于 Scribble**的两个菜单项。  按钮添加到名为的 **帮助**新面板。  
  
#### 添加帮助窗口  
  
1.  从 **工具箱**中，将 **面板** 拖到 **主页** 类别。  然后拖动两到面板的 **按钮**。  
  
2.  单击面板改变它的属性。  将**“标题”**更改为 `Help`。  
  
3.  单击第一个按钮。  `帮助主题`于 `ID_HELP_FINDER`更改的 **标题** 和 **ID**。  
  
4.  单击第二个按钮。  `关于 Scribble…`于 `ID_APP_ABOUT`更改的 **标题** 和 **ID**。  
  
5.  保存改变的，然后生成并运行应用程序。  应显示一 **帮助** 面板包含两个功能区按钮。  
  
    > [!IMPORTANT]
    >  当单击按钮时，**帮助主题** Scribble 应用程序中打开压缩 HTML \(.htm\) .chm 帮助文件名为 *your\_project\_name*。  因此，项目，则未命名组，必须将帮助文件重命名为项目名称。  
  
 \[[各节内容](#top)\]  
  
##  <a name="addPenPanel"></a> 将钢笔添加到功能区面板  
 现在，请添加一个面板到控制粗细和钢笔的颜色显示的按钮。  此面板中切换之间和粗出错的 Pen 的复选框。  其功能类似 Scribble 应用程序的 **重行** 菜单项。  
  
 原始 Scribble 应用程序允许从出现的对话框中的用户选择钢笔的宽度在用户菜单上单击 **钢笔的宽度**。  由于功能区栏有放置新控件的充足的空间，使用功能区上，的这两个组合框可以替换"对话框。  一个框组合调整出错的钢笔的宽度，并且另一个组合框的大小。钢笔的宽度。  
  
#### 将钢笔工具和组合框添加到功能区  
  
1.  从 **工具箱**中，将 **面板** 拖到 **主页** 类别。  然后将 **复选框** 和 **组合框** 两到面板中。  
  
2.  单击面板改变它的属性。  将**“标题”**更改为 `Pen`。  
  
3.  单击复选框。  `浓厚使用`于 `ID_PEN_THICK_OR_THIN`更改的 **标题** 和 **ID**。  
  
4.  单击第一组合框。  `细钢笔`的 **标题** 更改为 `ID_PEN_THIN_WIDTH`，**ID** 的，**文本** `2`的 `Drop List`，**类型** 的和 **数据** `1; 2; 3; 4; 5; 6; 7; 8; 9;`的。  
  
5.  单击第二组合框。  `粗钢笔`的 **标题** 更改为 `ID_PEN_THICK_WIDTH`，**ID** 的，**文本** `2`的 `Drop List`，**类型** 的和 **数据** `5; 6; 7; 8; 9;10;11;12;13;14;15;16;17;18;19;20;`的。  
  
6.  新的组合框不对应任何现有的菜单项。  因此，必须创建钢笔每个选项的菜单项。  
  
    1.  在 **资源视图** 窗口，请打开 IDR\_SCRIBBTYPE 菜单资源。  
  
    2.  单击 **笔** 打开菜单**en** 的减速。  然后单击 **请在此处键入** 并键入 `Thi&n 钢笔`。  
  
    3.  右击刚键入的文本 **属性** 打开窗口，然后将 ID 属性设置为 `ID_PEN_THIN_WIDTH`。  
  
    4.  您还必须创建钢笔菜单项的事件处理程序。  右击 **Thi&n 钢笔** 菜单项创建 **添加事件处理程序**然后单击。  **事件处理程序向导** 中显示。  
  
    5.  在 **类列表** 框在向导中，选择 **CScribbleDoc** 然后单击 **添加编辑 \(A\)**。  这将创建一个名为 `CScribbleDoc::OnPenThinWidth`的事件处理程序。  
  
    6.  将下列代码添加到 `CScribbleDoc::OnPenThinWidth`。  
  
        ```  
        // Get a pointer to the ribbon bar  
        CMFCRibbonBar* pRibbon = ((CMDIFrameWndEx*) AfxGetMainWnd())->GetRibbonBar();  
        ASSERT_VALID(pRibbon);  
        // Get a pointer to the Thin Width combo box  
        CMFCRibbonComboBox* pThinComboBox = DYNAMIC_DOWNCAST(  
           CMFCRibbonComboBox, pRibbon->FindByID(ID_PEN_THIN_WIDTH));  
        //Get the selected value  
        int nCurSel = pThinComboBox->GetCurSel();  
        if (nCurSel >= 0)  
        {  
           m_nThinWidth = atoi(pThinComboBox->GetItem(nCurSel));  
        }  
        // Create a new pen using the selected width  
        ReplacePen();    
        ```  
  
7.  接下来，创建一菜单项与事件处理程序。的 Pen。  
  
    1.  在 **资源视图** 窗口，请打开 IDR\_SCRIBBTYPE 菜单资源。  
  
    2.  单击 **笔** 打开菜单钢笔菜单。  然后单击 **请在此处键入** 并键入 `Thic&k 钢笔`。  
  
    3.  右击您键入 **属性** 窗口显示的文本。  将 ID 属性设置为 `ID_PEN_THICK_WIDTH`。  
  
    4.  右击 **粗钢笔 菜单项创建** 添加事件处理程序然后单击。  **事件处理程序向导** 中显示。  
  
    5.  在 **类列表** 框在向导中，选择 **CScribbleDoc** 然后单击 **添加编辑 \(A\)**。  这将创建一个名为 `CScribbleDoc::OnPenThickWidth`的事件处理程序。  
  
    6.  将下列代码添加到 `CScribbleDoc::OnPenThickWidth`。  
  
        ```  
        // Get a pointer to the ribbon bar  
        CMFCRibbonBar* pRibbon = ((CMDIFrameWndEx *) AfxGetMainWnd())->GetRibbonBar();  
        ASSERT_VALID(pRibbon);  
        CMFCRibbonComboBox* pThickComboBox = DYNAMIC_DOWNCAST(  
           CMFCRibbonComboBox, pRibbon->FindByID(ID_PEN_THICK_WIDTH));  
        // Get the selected value  
        int nCurSel = pThickComboBox->GetCurSel();  
        if (nCurSel >= 0)  
        {  
           m_nThickWidth = atoi(pThickComboBox->GetItem(nCurSel));  
        }  
        // Create a new pen using the selected width  
        ReplacePen();  
        ```  
  
8.  保存改变的，然后生成并运行应用程序。  应显示新按钮和组合框。  使用图形不同的 Pen 宽度的尝试。  
  
 \[[各节内容](#top)\]  
  
##  <a name="addColorButton"></a> 添加颜色钢笔按钮添加到面板  
 接下来，请将颜色允许用户是一个对象。[CMFCRibbonColorButton](../mfc/reference/cmfcribboncolorbutton-class.md)  
  
#### 添加颜色按钮添加到钢笔面板  
  
1.  将颜色按钮之前，请创建它的一个菜单项。  在 **资源视图** 窗口，请打开 IDR\_SCRIBBTYPE 菜单资源。  单击**钢笔**菜单项以打开该菜单。  然后单击 **请在此处键入** 并键入 `&Color`。  右击您键入 **属性** 窗口显示的文本。  更改ID到`ID_PEN_COLOR`。  
  
2.  现在添加颜色按钮。  从 **工具箱**中，将 **颜色按钮** 拖到 **笔** 面板。  
  
3.  单击颜色按钮。  **标题** 更改为 `Color`，将设置为 `ID_PEN_COLOR`，将 `True`的 **简单 查找**，**索引大图像** 为 `1`和 **拆分模式** 的 **ID** 设置为 `False`。  
  
4.  保存改变的，然后生成并运行应用程序。  在 **笔** "面板应显示新颜色按钮。  但是，它，因为它没有，事件处理程序无法使用。  以下步骤显示如何添加颜色按钮的事件处理程序。  
  
 \[[各节内容](#top)\]  
  
##  <a name="addColorMember"></a> 添加颜色文档成员添加到类  
 由于原始 Scribble 应用程序没有颜色钢笔，您必须编写自己实现的。  若要将文档存储更改笔的颜色，请添加新成员添加到文档，则 `CscribbleDoc.`类  
  
#### 添加颜色成员添加到文档类  
  
1.  在 scribdoc.h，`CScribbleDoc` 类，找到 `// Attributes` 节。  在 `m_nThickWidth` 数据成员的定义之后添加以下代码行。  
  
    ```  
    // Current pen color  
    COLORREF   m_penColor;  
    ```  
  
2.  每个文档包含一个列表升火用户已绘制。  每个笔画由 `CStroke` 对象定义。  `CStroke` 类包含有关钢笔颜色的信息。  因此，必须修改该类。  在 scribdoc.h，在 `CStroke` 类中，在 `m_nPenWidth` 数据成员的定义之后添加以下代码行。  
  
    ```  
    // Pen color for the stroke  
    COLORREF   m_penColor;  
    ```  
  
3.  在 scribdoc.h，将参数指定宽度和颜色新的 `CStroke` 构造函数。  在 `CStroke(UINT nPenWidth);` 报表之后添加以下代码。  
  
    ```  
    CStroke(UINT nPenWidth, COLORREF penColor);  
    ```  
  
4.  在 scribdoc.cpp，请将新的 `CStroke` 添加构造函数的实现。  在 `CStroke::CStroke(UINT nPenWidth)` 的构造函数实现的末尾，添加以下代码。  
  
    ```  
    // Constructor that uses the document's current width and color  
    CStroke::CStroke(UINT nPenWidth, COLORREF penColor)  
    {  
       m_nPenWidth = nPenWidth;  
       m_penColor = penColor;  
       m_rectBounding.SetRectEmpty();  
    }  
    ```  
  
5.  如下更改 `CStroke::DrawStroke` 方法的第二行。  
  
    ```  
    if (!penStroke.CreatePen(PS_SOLID, m_nPenWidth, m_penColor))  
    ```  
  
6.  设置钢笔类文档的默认颜色。  在 scribdoc.cpp，将下面一行添加到 `CScribbleDoc::InitDocument`中，在 `m_nThickWidth = 5;` 语句之后。  
  
    ```  
    // default pen color is black  
    m_penColor = RGB(0,0,0);   
    ```  
  
7.  在 scribdoc.cpp 中，更改 `CScribbleDoc::NewStroke` 方法中的第一行。下面。  
  
    ```  
    CStroke* pStrokeItem = new CStroke(m_nPenWidth, m_penColor);  
    ```  
  
8.  更改 `CScribbleDoc::ReplacePen` 方法中的最后一行。下面。  
  
    ```  
    m_penCur.CreatePen(PS_SOLID, m_nPenWidth, m_penColor);  
    ```  
  
9. 已添加一步中的 `m_penColor` 成员。  现在，创建将成员的颜色按钮的事件处理程序。  
  
    1.  在 **资源视图** 窗口，请打开 IDR\_SCRIBBTYPE 菜单资源。  
  
    2.  右击 **Color** 菜单项并单击 **添加事件处理程序。**。  出现 **事件处理程序向导**。  
  
    3.  在 **类列表** 框在向导中，选择 **CScribbleDoc** 然后单击 **添加编辑 \(A\)**按钮。  此操作将创建 `CScribbleDoc::OnPenColor` 事件处理程序。  
  
10. 使用下面的代码替换 `CScribbleDoc::OnPenColor` 事件处理程序中的注释：  
  
    ```  
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
  
11. 保存改变的，然后生成并运行应用程序。  您应该能按颜色按钮和更改钢笔的颜色。  
  
 \[[各节内容](#top)\]  
  
##  <a name="initPenSave"></a> 初始化钢笔和保存首选项  
 接下来，请初始化钢笔的颜色和宽度。  最后，和保存从文件中加载一颜色绘制。  
  
#### 初始化功能区栏上的控件  
  
1.  初始化在功能区栏的 Pen。  
  
     将以下代码添加到 scribdoc.cpp，`CScribbleDoc::InitDocument` 方法，在 `m_sizeDoc = CSize(200,200)` 语句之后。  
  
    ```  
    // Reset the ribbon UI to its initial values  
    CMFCRibbonBar* pRibbon =   
       ((CMDIFrameWndEx*) AfxGetMainWnd())->GetRibbonBar();  
    ASSERT_VALID(pRibbon);  
    CMFCRibbonColorButton* pColorBtn = DYNAMIC_DOWNCAST(  
       CMFCRibbonColorButton,   
       pRibbon->FindByID(ID_PEN_COLOR));  
    // Set ColorButton to black  
    pColorBtn->SetColor(RGB(0,0,0));    
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
  
2.  保存绘制到文件中的一种颜色。  将以下代码添加到 scribdoc.cpp，`CStroke::Serialize` 方法，在 `ar << (WORD)m_nPenWidth;` 语句之后。  
  
    ```  
    ar << (COLORREF)m_penColor;  
    ```  
  
3.  最后，从文件中加载一颜色绘制。  在 `CStroke::Serialize` 方法中，添加以下代码行，在 `m_nPenWidth = w;` 报表之后。  
  
    ```  
    ar >> m_penColor;  
    ```  
  
4.  现在请图形在颜色并保存绘制到文件。  
  
 \[[各节内容](#top)\]  
  
## 结束语  
 在更新应用 MFC 随意画图程序。  当修改现有应用程序中时，请使用本演练作为指南。  
  
## 请参阅  
 [演练](../mfc/walkthroughs-mfc.md)   
 [演练：更新 MFC 随意画图应用程序（第 1 部分）](../mfc/walkthrough-updating-the-mfc-scribble-application-part-1.md)