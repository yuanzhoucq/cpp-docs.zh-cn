---
title: "演练： 更新 MFC 随意画图应用程序 （第 2 部分） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: walkthroughs [MFC]
ms.assetid: 602df5c2-17d4-4cd9-8cf6-dff652c4cae5
caps.latest.revision: "36"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c4213bcc0321749ddda1ee0b85f577b01044bfc6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="walkthrough-updating-the-mfc-scribble-application-part-2"></a>演练：更新 MFC 随意画图应用程序（第 2 部分）
[第 1 部分](../mfc/walkthrough-updating-the-mfc-scribble-application-part-1.md)本演练介绍了如何将 Office Fluent 功能区添加到经典自由曲线应用程序。 本部分将显示如何添加功能区面板和控件，用户可以使用而不是菜单和命令。  
  
## <a name="prerequisites"></a>先决条件  
 [Visual C++ 示例](../visual-cpp-samples.md)  
  
##  <a name="top"></a> 部分  
 本部分演练包含以下部分：  
  
- [向功能区添加新的面板](#addnewpanel)  
  
- [将帮助面板添加到功能区](#addhelppanel)  
  
- [将钢笔面板添加到功能区](#addpenpanel)  
  
- [添加到功能区颜色按钮](#addcolorbutton)  
  
- [将颜色成员添加到文档类](#addcolormember)  
  
- [初始化钢笔和保存首选项](#initpensave)  
  
##  <a name="addnewpanel"></a>向功能区添加新的面板  
 这些步骤演示了如何添加**视图**面板，其中包含控制工具栏和状态栏的可见性的两个复选框以及**窗口**包含垂直的拆分面板控制的创建和排列多文档界面 (MDI) windows 的按钮。  
  
#### <a name="to-add-a-view-panel-and-window-panel-to-the-ribbon-bar"></a>若要将视图面板和窗口面板添加到功能区栏  
  
1.  创建名为面板`View`，它具有两个复选框的切换状态栏和工具栏。  
  
    1.  从**工具箱**，拖动**面板**到**主页**类别。 然后将两个**复选框**到面板。  
  
    2.  单击要修改其属性的面板。 更改**标题**到`View`。  
  
    3.  单击第一个的复选框，以修改其属性。 更改**ID**到`ID_VIEW_TOOLBAR`和**标题**到`Toolbar`。  
  
    4.  单击第二个的复选框，以修改其属性。 更改**ID**到`ID_VIEW_STATUS_BAR`和**标题**到`Status Bar`。  
  
2.  创建名为面板`Window`具有拆分按钮。 当用户单击拆分按钮时，快捷菜单会显示已在随意画图应用程序中定义的三个命令。  
  
    1.  从**工具箱**，拖动**面板**到**主页**类别。 然后拖动**按钮**到面板。  
  
    2.  单击要修改其属性的面板。 更改**标题**到`Window`。  
  
    3.  单击按钮。 更改**标题**到`Windows`，**密钥**到`w`，**大图像索引**到`1`，和**拆分模式**到`False`。 然后单击省略号 (**...**) 旁边**菜单项**以打开**项编辑器**对话框。  
  
    4.  单击**添加**三次以添加三个按钮。  
  
    5.  单击第一个按钮，然后更改**标题**到`New Window`，和**ID**到`ID_WINDOW_NEW`。  
  
    6.  单击第二个按钮，然后更改**标题**到`Cascade`，和**ID**到`ID_WINDOW_CASCADE`。  
  
    7.  单击第三个按钮，然后更改**标题**到`Tile`，和**ID**到`ID_WINDOW_TILE_HORZ`。  
  
3.  保存更改，然后生成并运行应用程序。 **视图**和**窗口**应显示面板。 单击的按钮，以确认它们正常。  
  
 [[部分](#top)]  
  
##  <a name="addhelppanel"></a>将帮助面板添加到功能区  
 现在，你可以将分配到命名的功能区按钮随意画图应用程序中定义的两个菜单项**帮助主题**和**有关 Scribble**。 这些按钮将添加到名为的新面板**帮助**。  
  
#### <a name="to-add-a-help-panel"></a>若要添加的帮助面板  
  
1.  从**工具箱**，拖动**面板**到**主页**类别。 然后将两个**按钮**到面板。  
  
2.  单击要修改其属性的面板。 更改**标题**到`Help`。  
  
3.  单击第一个按钮。 更改**标题**到`Help Topics`，和**ID**到`ID_HELP_FINDER`。  
  
4.  单击第二个按钮。 更改**标题**到`About Scribble...`，和**ID**到`ID_APP_ABOUT`。  
  
5.  保存更改，然后生成并运行应用程序。 A**帮助**应显示包含两个功能区按钮的面板。  
  
    > [!IMPORTANT]
    >  当你单击**帮助主题**单击按钮，随意画图应用程序将打开名为的压缩 (.chm) HTML 帮助文件*your_project_name*。 chm。 因此，如果你的项目未命名 Scribble，你必须将重命名的帮助文件为你的项目名称。  
  
 [[部分](#top)]  
  
##  <a name="addpenpanel"></a>将钢笔面板添加到功能区  
 现在，添加一个面板，以显示控制粗细和的钢笔颜色的按钮。 此面板包含一个复选框，在粗线和细钢笔之间切换。 其功能类似于**粗线**随意画图应用程序中的菜单项。  
  
 原始随意画图应用程序使用户可以从对话框中，当用户单击时显示选择钢笔宽度**钢笔宽度**菜单上。 由于功能区栏具有提供足够空间的新控件，可通过使用功能区上的两个组合框来代替对话框。 一个组合框调整精简钢笔的宽度和其他组合框调整密集钢笔的宽度。  
  
#### <a name="to-add-a-pen-panel-and-combo-boxes-to-the-ribbon"></a>若要向功能区添加钢笔面板和组合框  
  
1.  从**工具箱**，拖动**面板**到**主页**类别。 然后拖动**复选框**和两个**组合框**到面板。  
  
2.  单击要修改其属性的面板。 更改**标题**到`Pen`。  
  
3.  单击复选框。 更改**标题**到`Use Thick`，和**ID**到`ID_PEN_THICK_OR_THIN`。  
  
4.  单击第一个组合框。 更改**标题**到`Thin Pen`， **ID**到`ID_PEN_THIN_WIDTH`，**文本**到`2`，**类型**到`Drop List`，和**数据**到`1;2;3;4;5;6;7;8;9;`。  
  
5.  单击第二个的组合框。 更改**标题**到`Thick Pen`， **ID**到`ID_PEN_THICK_WIDTH`，**文本**到`5`，**类型**到`Drop List`，和**数据**到`5;6;7;8;9;10;11;12;13;14;15;16;17;18;19;20;`。  
  
6.  新的组合框不对应于任何现有的菜单项。 因此，你必须创建钢笔的每个选项的菜单项。  
  
    1.  在**资源视图**窗口中，打开 IDR_SCRIBBTYPE 菜单资源。  
  
    2.  单击**钢笔**以打开 p**en**菜单。 然后单击**此处键入**和类型`Thi&n Pen`。  
  
    3.  右键单击你刚刚键入的用于打开文本**属性**窗口，然后更改 ID 属性`ID_PEN_THIN_WIDTH`。  
  
    4.  你还必须创建的事件处理程序的每一笔菜单项。 右键单击**此应用和 n 钢笔**你刚刚创建，然后单击的菜单项**添加事件处理程序**。 **事件处理程序向导**显示。  
  
    5.  在**类列表**框中的向导中，选择**CScribbleDoc** ，然后单击**添加和编辑**。 这将创建名为一个事件处理程序`CScribbleDoc::OnPenThinWidth`。  
  
    6.  将下列代码添加到 `CScribbleDoc::OnPenThinWidth`。  
  
 ``` *获取一个指向功能区栏 CMFCRibbonBar* pRibbon = ((CMDIFrameWndEx*) AfxGetMainWnd())-> GetRibbonBar();ASSERT_VALID(pRibbon);*/ / 获取指向精简宽度组合框 CMFCRibbonComboBox 的指针*pThinComboBox = DYNAMIC_DOWNCAST (CMFCRibbonComboBox，pRibbon-> FindByID(ID_PEN_THIN_WIDTH)); * //Get 选定的值  
    int nCurSel = pThinComboBox-> GetCurSel();如果 (nCurSel > = 0)  
{  
m_nThinWidth = atoi （pThinComboBox-> GetItem(nCurSel));

 } * / / 创建新的笔使用所选的宽度  
    ReplacePen();

 ```  
  
7.  Next, create a menu item and event handlers for the thick pen.  
  
    1.  In the **Resource View** window, open the IDR_SCRIBBTYPE menu resource.  
  
    2.  Click **Pen** to open the pen menu. Then click **Type Here** and type `Thic&k Pen`.  
  
    3.  Right-click the text that you just typed to display the **Properties** window. Change the ID property to `ID_PEN_THICK_WIDTH`.  
  
    4.  Right-click the **Thick Pen** menu item that you just created and then click **Add Event Handler**. The **Event Handler Wizard** is displayed.  
  
    5.  In the **Class list** box of the wizard, select **CScribbleDoc** and then click **Add and Edit**. This creates an event handler named `CScribbleDoc::OnPenThickWidth`.  
  
    6.  Add the following code to `CScribbleDoc::OnPenThickWidth`.  
  
 ``` *// Get a pointer to the ribbon bar  
    CMFCRibbonBar* pRibbon = ((CMDIFrameWndEx *) AfxGetMainWnd())->GetRibbonBar();
ASSERT_VALID(pRibbon);

 CMFCRibbonComboBox* pThickComboBox = DYNAMIC_DOWNCAST(
    CMFCRibbonComboBox, pRibbon->FindByID(ID_PEN_THICK_WIDTH));
*// Get the selected value  
    int nCurSel = pThickComboBox->GetCurSel();
if (nCurSel>= 0)  
 {  
    m_nThickWidth = atoi(pThickComboBox->GetItem(nCurSel));

 } *// Create a new pen using the selected width  
    ReplacePen();

 ```  
  
8.  保存更改，然后生成并运行应用程序。 应显示新按钮和组合框。 请尝试使用不同的钢笔宽度 scribble。  
  
 [[部分](#top)]  
  
##  <a name="addcolorbutton"></a>将颜色按钮添加到钢笔面板  
 接下来，添加[CMFCRibbonColorButton](../mfc/reference/cmfcribboncolorbutton-class.md)对象，使用户能够自由曲线的颜色的颜色。  
  
#### <a name="to-add-a-color-button-to-the-pen-panel"></a>若要将颜色按钮添加到钢笔面板  
  
1.  在添加此颜色按钮之前，请为其创建菜单项。 在**资源视图**窗口中，打开 IDR_SCRIBBTYPE 菜单资源。 单击**钢笔**要打开钢笔菜单的菜单项。 然后单击**此处键入**和类型`&Color`。 右键单击你刚刚键入要显示的文本**属性**窗口。 将 ID 更改为`ID_PEN_COLOR`。  
  
2.  现在，添加此颜色按钮。 从**工具箱**，拖动**颜色按钮**到**钢笔**面板。  
  
3.  单击此颜色按钮。 更改**标题**到`Color`， **ID**到`ID_PEN_COLOR`， **SimpleLook**到`True`，**大图像索引**到`1`，和**拆分模式**到`False`。  
  
4.  保存更改，然后生成并运行应用程序。 新的颜色按钮应显示在**钢笔**面板。 但是，它不用于因为它还没有一个事件处理程序。 下一步的步骤演示了如何添加此颜色按钮事件处理程序。  
  
 [[部分](#top)]  
  
##  <a name="addcolormember"></a>将颜色成员添加到文档类  
 因为原始随意画图应用程序并没有颜色的笔，你必须为它们编写实现。 若要存储文档的钢笔颜色，请将新成员添加到的文档类，`CscribbleDoc.`  
  
#### <a name="to-add-a-color-member-to-the-document-class"></a>若要将颜色成员添加到文档类  
  
1.  在 scribdoc.h，在`CScribbleDoc`类中，查找`// Attributes`部分。 添加以下代码行后的定义`m_nThickWidth`数据成员。  
  
 ' * / / 当前钢笔颜色  
    COLORREF m_penColor;  
 ```  
  
2.  Every document contains a list of stokes that the user has already drawn. Every stroke is defined by a `CStroke` object. The `CStroke` class does not include information about pen color. Therefore, you must modify the class. In scribdoc.h, in the `CStroke` class, add the following lines of code after the definition of the `m_nPenWidth` data member.  
  
 ``` *// Pen color for the stroke  
    COLORREF m_penColor;  
 ```  
  
3.  在 scribdoc.h，添加一个新`CStroke`其参数指定宽度和颜色的构造函数。 添加以下行后的代码`CStroke(UINT nPenWidth);`语句。  
  
 ```  
    CStroke(UINT nPenWidth, COLORREF penColor);

 ```  
  
4.  在 scribdoc.cpp，添加的新实现`CStroke`构造函数。 将以下代码添加后的实现`CStroke::CStroke(UINT nPenWidth)`构造函数。  
  
 ' * / / 使用文档的构造函数的当前宽度和颜色  
    CStroke::CStroke （UINT nPenWidth，COLORREF penColor）  
 {  
    m_nPenWidth = nPenWidth;  
    m_penColor = penColor;  
    m_rectBounding.SetRectEmpty();

 }  
 ```  
  
5.  Change the second line of the `CStroke::DrawStroke` method as follows.  
  
 ```  
    如果 (！ penStroke.CreatePen (PS_SOLID，m_nPenWidth、 m_penColor))  
 ```  
  
6.  Set the default pen color for the document class. In scribdoc.cpp, add the following lines to `CScribbleDoc::InitDocument`, after the `m_nThickWidth = 5;` statement.  
  
 ``` *// default pen color is black  
    m_penColor = RGB(0,
    0,
    0);

 ```  
  
7.  在 scribdoc.cpp，更改的第一行`CScribbleDoc::NewStroke`于以下的方法。  
  
 ```  
    CStroke* pStrokeItem = new CStroke(m_nPenWidth, m_penColor);

 ```  
  
8.  更改的最后一行`CScribbleDoc::ReplacePen`于以下的方法。  
  
 ```  
    m_penCur.CreatePen(PS_SOLID,
    m_nPenWidth,
    m_penColor);

 ```  
  
9. 你添加`m_penColor`上一步中的成员。 现在，创建的事件处理程序的成员设置此颜色按钮。  
  
    1.  在**资源视图**窗口中，打开 IDR_SCRIBBTYPE 菜单资源。  
  
    2.  右键单击**颜色**菜单项并单击**添加事件处理程序**。 **事件处理程序向导**显示。  
  
    3.  在**类列表**框中的向导中，选择**CScribbleDoc** ，然后单击**添加和编辑**按钮。 这将创建`CScribbleDoc::OnPenColor`事件处理程序存根 （stub)。  
  
10. 替换为存根`CScribbleDoc::OnPenColor`事件处理程序替换为以下代码。  
  
 ```  
    void CScribbleDoc::OnPenColor()  
 { *// Change pen color to reflect color button's current selection  
    CMFCRibbonBar* pRibbon = ((CMDIFrameWndEx*) AfxGetMainWnd())->GetRibbonBar();
ASSERT_VALID(pRibbon);

 CMFCRibbonColorButton* pColorBtn = DYNAMIC_DOWNCAST(
    CMFCRibbonColorButton, pRibbon->FindByID(ID_PEN_COLOR));

    m_penColor = pColorBtn->GetColor();
*// Create new pen using the selected color  
    ReplacePen();

 }  
 ```  
  
11. 保存更改然后生成并运行应用程序。 你应能够按颜色按钮，并更改的钢笔颜色。  
  
 [[部分](#top)]  
  
##  <a name="initpensave"></a>初始化钢笔和保存首选项  
 接下来，初始化的颜色和宽度的笔。 最后，保存并加载从文件中绘制的颜色。  
  
#### <a name="to-initialize-controls-on-the-ribbon-bar"></a>若要初始化的功能区栏上的控件  
  
1.  初始化功能区栏上的钢笔。  
  
     将以下代码添加到 scribdoc.cpp，，在`CScribbleDoc::InitDocument`方法之后，`m_sizeDoc = CSize(200,200)`语句。  
  
 ```*/ / 将功能区用户界面重置为其初始值 CMFCRibbonBar* pRibbon = ((CMDIFrameWndEx*) AfxGetMainWnd())-> GetRibbonBar();ASSERT_VALID(pRibbon);

 CMFCRibbonColorButton * pColorBtn = DYNAMIC_DOWNCAST （CMFCRibbonColorButton，pRibbon-> FindByID(ID_PEN_COLOR));* / 设置为黑色的 ColorButton  
    pColorBtn-> SetColor (RGB （0，0，0）);

 CMFCRibbonComboBox * pThinComboBox = DYNAMIC_DOWNCAST （CMFCRibbonComboBox，pRibbon-> FindByID(ID_PEN_THIN_WIDTH));* / 设置为 2 的精简钢笔组合框  
    pThinComboBox-> SelectItem(1);

 CMFCRibbonComboBox * pThickComboBox = DYNAMIC_DOWNCAST （CMFCRibbonComboBox，pRibbon-> FindByID(ID_PEN_THICK_WIDTH));* / 设置为 5 的密集钢笔组合框  
    pThickComboBox-> SelectItem(0);

 ```  
  
2.  Save a color drawing to a file. Add the following statement to scribdoc.cpp, in the `CStroke::Serialize` method, after the `ar << (WORD)m_nPenWidth;` statement.  
  
 ```  
    ar << (COLORREF) m_penColor;  
 ```  
  
3.  Finally, load a color drawing from a file. Add the following line of code, in the `CStroke::Serialize` method, after the `m_nPenWidth = w;` statement.  
  
 ```  
    ar >> m_penColor;  
 ```  
  
4.  Now scribble in color and save your drawing to a file.  
  
 [[Sections](#top)]  
  
## Conclusion  
 You have updated the MFC Scribble application. Use this walkthrough as a guide when you modify your existing applications.  
  
## See Also  
 [Walkthroughs](../mfc/walkthroughs-mfc.md)   
 [Walkthrough: Updating the MFC Scribble Application (Part 1)](../mfc/walkthrough-updating-the-mfc-scribble-application-part-1.md)

