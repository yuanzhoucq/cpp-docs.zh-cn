---
title: 演练： 向 MFC 项目添加动画 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- animation [MFC]
- MFC, animation
ms.assetid: 004f832c-9fd5-4f88-9ca9-ae65dececdc2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e8ae7496daf6827a6be7769d60af10bca45f7a3d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33384744"
---
# <a name="walkthrough-adding-animation-to-an-mfc-project"></a>演练：向 MFC 项目添加动画
本演练介绍如何将基本的动画的对象添加到 Visual c + +，Microsoft 基础类库 (MFC) 项目。  
  
 本演练演示如何完成这些任务：  
  
-   创建 MFC 应用程序。  
  
-   添加一个菜单，然后添加命令来启动和停止动画。  
  
-   创建启动和停止命令的处理程序。  
  
-   向项目添加动画的对象。  
  
-   Center 窗口中经过动画处理的对象。  
  
-   验证结果。  
  
 [!INCLUDE[note_settings_general](../mfc/includes/note_settings_general_md.md)]  
  
## <a name="prerequisites"></a>系统必备  
 若要完成本演练，您必须具有 Visual Studio。  
  
### <a name="to-create-an-mfc-application"></a>若要创建 MFC 应用程序  
  
1.  在 **“文件”** 菜单上指向 **“新建”** ，然后单击 **“项目”**。  
  
2.  在**新项目**对话框中，在左窗格中下**已安装的模板**，展开**Visual c + +** ，然后选择**MFC**。 在中间窗格中，选择**MFC 应用程序**。 在“名称”框中键入 `MFCAnimationWalkthrough`。 单击 **“确定”**。  
  
3.  在**MFC 应用程序向导**对话框框中，确认**应用程序类型**是**多个文档**，**项目样式**是**Visual Studio**，和**文档/视图体系结构支持**选项。 单击 **“完成”**。  
  
### <a name="to-add-a-menu-and-then-add-commands-to-start-and-stop-an-animation"></a>若要添加一个菜单，然后添加命令来启动和停止动画  
  
1.  上**视图**菜单上，指向**其他窗口**，然后单击**资源视图**。  
  
2.  在**资源视图**，导航到**菜单**文件夹并将其打开。 双击`IDR_MFCAnimationWalTYPE`资源以将其打开以进行修改。  
  
3.  在菜单栏上，在**此处键入**框中，键入`A&nimation`创建动画菜单。  
  
4.  下**动画**中**此处键入**框中，键入`Start &Forward`创建转发启动命令。  
  
5.  下**转发启动**中**此处键入**框中，键入`Start &Backward`。  
  
6.  下**启动向后**中**此处键入**框中，键入`S&top`创建停止命令。  
  
7.  保存 MFCAnimationWalkthrough.rc 并将其关闭。  
  
8.  在**解决方案资源管理器**，双击以打开进行修改的 MainFrm.cpp。 在`CMainFrame::OnCreate`方法中，找到具有多个调用的部分`lstBasicCommands.AddTail`。 此部分中之后, 添加以下代码。  
  
 ```  
    lstBasicCommands.AddTail(ID_ANIMATION_STARTFORWARD);

 lstBasicCommands.AddTail(ID_ANIMATION_STARTBACKWARD);

    lstBasicCommands.AddTail(ID_ANIMATION_STOP);

 ```  
  
9. 保存该文件并将其关闭。  
  
### <a name="to-create-handlers-for-the-start-and-stop-commands"></a>创建处理程序开始和停止命令  
  
1.  上**项目**菜单上，单击**类向导**。  
  
2.  在**MFC 类向导**下**类名**，选择`CMFCAnimationWalkthroughView`。  
  
3.  上**命令**选项卡上，在**对象 Id**框中，选择`ID_ANIMATION_STARTFORWARD`，然后在**消息**框中，选择`COMMAND`。 单击**添加处理程序**。  
  
4.  在**添加成员函数**对话框中，单击**确定**。  
  
5.  在**对象 Id**框中，选择`ID_ANIMATION_STARTBACKWARD`，然后在**消息**框中，选择`COMMAND`。 单击**添加处理程序**。  
  
6.  在**添加成员函数**对话框中，单击**确定**。  
  
7.  在**对象 Id**框中，选择`ID_ANIMATION_STOP`，然后在**消息**框中，选择`COMMAND`。 单击**添加处理程序**，然后单击**确定**。  
  
8.  在**添加成员函数**对话框中，单击**确定**。  
  
9. 在**MFC 类向导**，单击**确定**。  
  
10. 保存 MFCAnimationWalkthroughView.cpp，这是在编辑器中打开，但不要将其关闭。  
  
### <a name="to-add-an-animated-object-to-the-project"></a>若要向项目添加动画的对象  
  
1.  在解决方案资源管理器中，双击 MFCAnimationWalkthroughView.h 打开进行修改。 之前的定义`CMFCAnimationWalkthroughView`类中，添加以下代码以创建一个自定义动画控制器，将处理与动画对象的计划冲突。  
  
 ```  
    class CCustomAnimationController : public CAnimationController  
 {  
    public: 
    CCustomAnimationController() 
 {  
 }  
 
    virtual BOOL OnHasPriorityTrim(CAnimationGroup* pGroupScheduled,
    CAnimationGroup* pGroupNew,
    UI_ANIMATION_PRIORITY_EFFECT priorityEffect)  
 {  
    return TRUE;  
 }  
 };  
 ```  
  
2.  在结束`CMFCAnimationWalkthroughView`类中，添加下面的代码。  
  
 ```  
    CCustomAnimationController m_animationController;  
    CAnimationColor m_animationColor;   
    CAnimationRect m_animationRect;  
 ```  
  
3.  后`DECLARE_MESSAGE_MAP()`行，添加以下代码。  
  
 ```  
    void Animate(BOOL bDirection);

 ```  
  
4.  保存该文件并将其关闭。  
  
5.  在 MFCAnimationWalkthroughView.cpp 后文件的顶部`#include`语句但任意类方法之前, 添加以下代码。  
  
 ```  
    static int nAnimationGroup = 0;  
    static int nInfoAreaHeight = 40;  
 ```  
  
6.  构造函数末尾`CMFCAnimationWalkthroughView`，添加以下代码。  
  
 ```  
    m_animationController.EnableAnimationTimerEventHandler();
m_animationController.EnablePriorityComparisonHandler(UI_ANIMATION_PHT_TRIM);

 
    m_animationColor = RGB(255,
    255,
    255);

    m_animationRect = CRect(0,
    0,
    0,
    0);

 
    m_animationColor.SetID(-1,
    nAnimationGroup);

    m_animationRect.SetID(-1,
    nAnimationGroup);

 
    m_animationController.AddAnimationObject(&m_animationColor);

 m_animationController.AddAnimationObject(&m_animationRect);

 ```  
  
7.  找到`CAnimationWalthroughView::PreCreateWindow`方法，然后将它替换为以下代码。  
  
 ```  
    BOOL CMFCAnimationWalkthroughView::PreCreateWindow(CREATESTRUCT& cs)  
 { *// TODO: Modify the Window class or styles here by modifying *//  the CREATESTRUCT cs  
 
    m_animationController.SetRelatedWnd(this);

 return CView::PreCreateWindow(cs);

 }  
 ```  
  
8.  找到`CAnimationWalkthroughView::OnDraw`方法，然后将它替换为以下代码。  
  
 ```  
    void CMFCAnimationWalkthroughView::OnDraw(CDC* pDC)  
 {  
    CMFCAnimationWalkthroughDoc* pDoc = GetDocument();
ASSERT_VALID(pDoc);

 if (!pDoc)  
    return; 
 *// TODO: add draw code for native data here  
    CMemDC dcMem(*pDC,
    this);

    CDC& dc = dcMem.GetDC();

 
    CRect rect;  
    GetClientRect(rect);

 
    dc.FillSolidRect(rect,
    GetSysColor(COLOR_WINDOW));

 
    CString strRGB;  
    strRGB.Format(_T("Fill Color is: %d; %d; %d"),
    GetRValue(m_animationColor),
    GetGValue(m_animationColor),
    GetBValue(m_animationColor));

 
    dc.DrawText(strRGB,
    rect,
    DT_CENTER);

    rect.top += nInfoAreaHeight;  
 
    CBrush br;  
 
    br.CreateSolidBrush(m_animationColor);

 CBrush* pBrushOld = dc.SelectObject(&br);

 
    dc.Rectangle((CRect)m_animationRect);

 dc.SelectObject(pBrushOld);

 }  
 ```  
  
9. 在文件末尾，添加以下代码。  
  
 ```  
    void CMFCAnimationWalkthroughView::Animate(BOOL bDirection)  
 {  
    static UI_ANIMATION_SECONDS duration = 3;  
    static DOUBLE dblSpeed = 35.;  
    static BYTE nStartColor = 50;  
    static BYTE nEndColor = 255;  
 
    BYTE nRedColorFinal = bDirection  nStartColor : nEndColor;  
    BYTE nGreenColorFinal = bDirection  nStartColor : nEndColor;  
    BYTE nBlueColorFinal = bDirection  nStartColor : nEndColor;  
 
    CLinearTransition* pRedTransition = new CLinearTransition(duration, (DOUBLE)nRedColorFinal);

    CSmoothStopTransition* pGreenTransition = new CSmoothStopTransition(duration, (DOUBLE)nGreenColorFinal);

    CLinearTransitionFromSpeed* pBlueTransition = new CLinearTransitionFromSpeed(dblSpeed, (DOUBLE)nBlueColorFinal);

 
    m_animationColor.AddTransition(pRedTransition,
    pGreenTransition,
    pBlueTransition);

 
    CRect rectClient;  
    GetClientRect(rectClient);

 rectClient.top += nInfoAreaHeight;  
 
    int nLeftFinal = bDirection  rectClient.left : rectClient.CenterPoint().x;  
    int nTopFinal = bDirection  rectClient.top : rectClient.CenterPoint().y;  
    int nRightFinal = bDirection  rectClient.right : rectClient.CenterPoint().x;  
    int nBottomFinal = bDirection  rectClient.bottom : rectClient.CenterPoint().y;  
 
    CLinearTransition* pLeftTransition = new CLinearTransition(duration,
    nLeftFinal);

    CLinearTransition* pTopTransition = new CLinearTransition(duration,
    nTopFinal);

    CLinearTransition* pRightTransition = new CLinearTransition(duration,
    nRightFinal);

    CLinearTransition* pBottomTransition = new CLinearTransition(duration,
    nBottomFinal);

 
    m_animationRect.AddTransition(pLeftTransition,
    pTopTransition,
    pRightTransition,
    pBottomTransition);

 
    CBaseKeyFrame* pKeyframeStart = CAnimationController::GetKeyframeStoryboardStart();
CKeyFrame* pKeyFrameEnd = m_animationController.CreateKeyframe(nAnimationGroup,
    pBlueTransition);

 
    pLeftTransition->SetKeyframes(pKeyframeStart,
    pKeyFrameEnd);

    pTopTransition->SetKeyframes(pKeyframeStart,
    pKeyFrameEnd);

    pRightTransition->SetKeyframes(pKeyframeStart,
    pKeyFrameEnd);

    pBottomTransition->SetKeyframes(pKeyframeStart,
    pKeyFrameEnd);

 
    m_animationController.AnimateGroup(nAnimationGroup);

 }  
 ```  
  
10. 上**项目**菜单上，单击**类向导**。  
  
11. 在**MFC 类向导**下**类名**，选择`CMFCAnimationWalkthroughView`。  
  
12. 上**消息**选项卡上，在**消息**框中，选择`WM_ERASEBKGND`，单击**添加处理程序**，然后单击**确定**。  
  
13. 在 MFCAnimationWalkthroughView.cpp 中的实现替换`OnEraseBkgnd`替换为以下代码以减少出现闪烁动画对象，而它重绘。  
  
 ```  
    BOOL CMFCAnimationWalkthroughView::OnEraseBkgnd(CDC* /*pDC*/)  
 {  
    return TRUE;  
 }  
 ```  
  
14. 替换的实现`CMFCAnimationWalkthroughView::OnAnimationStartforward`， `CMFCAnimationWalkthroughView::OnAnimationStartbackward`，和`CMFCAnimationWalkthroughView::OnAnimationStop`替换为以下代码。  
  
 ```  
    void CMFCAnimationWalkthroughView::OnAnimationStartforward()  
 {  
    Animate(TRUE);

 }  
 
    void CMFCAnimationWalkthroughView::OnAnimationStartbackward()  
 {  
    Animate(FALSE);

 }  
 
    void CMFCAnimationWalkthroughView::OnAnimationStop()  
 {  
    IUIAnimationManager* pManager = m_animationController.GetUIAnimationManager();
if (pManager != NULL)  
 {  
    pManager->AbandonAllStoryboards();

 }  
 }  
 
 ```  
  
15. 保存该文件并将其关闭。  
  
### <a name="to-center-the-animated-object-in-the-window"></a>到中心窗口中经过动画处理的对象  
  
1.  在**解决方案资源管理器**，双击 MFCAnimationWalkthroughView.h 打开进行修改。 在结束`CMFCAnimationWalkthroughView`类，紧随其后的定义`m_animationRect`，添加以下代码。  
  
 ```  
    BOOL m_bCurrentDirection;  
 ```  
  
2.  保存该文件并将其关闭。  
  
3.  上**项目**菜单上，单击**类向导**。  
  
4.  在**MFC 类向导**下**类名**，选择`CMFCAnimationWalkthroughView`。  
  
5.  上**消息**选项卡上，在**消息**框中，选择`WM_SIZE`，单击**添加处理程序**，然后单击**确定**。  
  
6.  在 MFCAnimationWalkthroughView.cpp，替换为代码`CMFCAnimationWalkthroughView::OnSize`替换为以下代码。  
  
 ```  
    void CMFCAnimationWalkthroughView::OnSize(UINT nType,
    int cx,
    int cy)  
 {  
    CView::OnSize(nType,
    cx,
    cy);

 
    CRect rect;  
    GetClientRect(rect);

 rect.top += nInfoAreaHeight;  
 
    CRect rectAnim = m_animationRect;  
    m_animationRect = CRect(CPoint(rect.CenterPoint().x - rectAnim.Width() / 2,   
    rect.CenterPoint().y - rectAnim.Height() / 2),   
    rectAnim.Size());

 
    if (m_animationController.IsAnimationInProgress())  
 {  
    Animate(m_bCurrentDirection);

 }  
 }  
 ```  
  
7.  构造函数的开头`CMFCAnimationWalkthroughView`，添加以下代码。  
  
 ```  
    m_bCurrentDirection = TRUE;  
 ```  
  
8.  开头的`CMFCAnimationWalkthroughView::Animate`方法，添加以下代码。  
  
 ```  
    m_bCurrentDirection = bDirection;  
 ```  
  
9. 保存该文件并将其关闭。  
  
### <a name="to-verify-the-results"></a>若要验证的结果  
  
1.  生成并运行应用程序。 上**动画**菜单上，单击**转发启动**。 矩形应显示，然后填上中心区域。 当你单击**启动向后**、 应颠倒动画，并单击**停止**，它应停止。 在动画运行时，应更改矩形的填充颜色，且应顶部的动画窗口显示当前颜色。  
  
## <a name="see-also"></a>请参阅  
 [演练](../mfc/walkthroughs-mfc.md)

