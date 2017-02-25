---
title: "演练：向 MFC 项目添加动画 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "动画 [MFC]"
  - "MFC, 动画"
ms.assetid: 004f832c-9fd5-4f88-9ca9-ae65dececdc2
caps.latest.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# 演练：向 MFC 项目添加动画
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此演练介绍如何将基本的动画对象添加到 Visual C\+\+ Microsoft 基础类库 \(MFC\) 项目中。  
  
 此演练演示如何完成以下这些任务：  
  
-   创建 MFC 应用程序。  
  
-   添加菜单，然后添加用于开始和停止动画的命令。  
  
-   为开始和停止命令创建处理程序。  
  
-   向项目中添加动画对象。  
  
-   使动画对象在窗口中居中。  
  
-   验证结果。  
  
 [!INCLUDE[note_settings_general](../mfc/includes/note_settings_general_md.md)]  
  
## 系统必备  
 若要完成本演练，您必须具有：Visual Studio。  
  
### 创建 MFC 应用程序  
  
1.  在**“文件”**菜单上指向**“新建”**，然后单击**“项目”**。  
  
2.  在**“新建项目”**对话框左窗格的**“已安装的模板”**下，展开**“Visual C\+\+”**，然后选择**“MFC”**。  在中间窗格中，选择**“MFC 应用程序”**。  在**“名称”**框中，键入 `MFCAnimationWalkthrough`。  单击**“确定”**。  
  
3.  在**“MFC 应用程序向导”**对话框中，确认**“应用程序类型”**为**“多个文档”**，**“项目样式”**为**“Visual Studio”**，并且选择了**“文档\/视图结构支持”**选项。  单击**“完成”**。  
  
### 添加菜单，然后添加用于开始和停止动画的命令  
  
1.  在**“视图”**菜单上，指向**“其他窗口”**，然后单击**“资源视图”**。  
  
2.  在**“资源视图”**中，导航到**“菜单”**文件夹并打开它。  双击 `IDR_MFCAnimationWalTYPE` 资源以打开它进行修改。  
  
3.  在菜单栏上的**“请在此处键入”**框中，键入`A&nimation` 以创建“Animation”（动画）菜单。  
  
4.  在**“Animation”（动画）**下的**“请在此处键入”**框中，键入`Start &Forward` 以创建“Start Forward”（开始前进）命令。  
  
5.  在**“Start Forward”（开始前进）**下的**“请在此处键入”**框中，键入`Start &Backward`。  
  
6.  在**“Start Backward”（开始后退）**下的**“请在此处键入”**框中，键入`S&top` 来创建一个停止命令。  
  
7.  保存 MFCAnimationWalkthrough.rc 并关闭它。  
  
8.  在**“解决方案资源管理器”**中，双击“MainFrm.cpp”以打开它进行修改。  在 `CMainFrame::OnCreate` 方法中，找到具有对 `lstBasicCommands.AddTail` 的多次调用的节。  在紧接该节之后添加下列代码。  
  
    ```  
    lstBasicCommands.AddTail(ID_ANIMATION_STARTFORWARD);  
    lstBasicCommands.AddTail(ID_ANIMATION_STARTBACKWARD);  
    lstBasicCommands.AddTail(ID_ANIMATION_STOP);  
    ```  
  
9. 保存文件并将其关闭。  
  
### 为开始和停止命令创建处理程序  
  
1.  在**“项目”**菜单上单击**“类向导”**。  
  
2.  在**“MFC 类向导”**中的**“类名”**下，选择 `CMFCAnimationWalkthroughView`。  
  
3.  在**“命令”**选项卡上的**“对象 ID”**框中，选择 `ID_ANIMATION_STARTFORWARD`，然后在**“消息”**框中，选择 `COMMAND`。  单击**“添加处理程序”**。  
  
4.  在**“添加成员函数”**对话框中，单击**“确定”**。  
  
5.  在**“对象 ID”**框中选择 `ID_ANIMATION_STARTBACKWARD`，然后在**“消息”**框中选择 `COMMAND`。  单击**“添加处理程序”**。  
  
6.  在**“添加成员函数”**对话框中，单击**“确定”**。  
  
7.  在**“对象 ID”**框中选择 `ID_ANIMATION_STOP`，然后在**“消息”**框中选择 `COMMAND`。  单击**“添加处理程序”**，然后单击**“确定”**。  
  
8.  在**“添加成员函数”**对话框中，单击**“确定”**。  
  
9. 在**“MFC 类向导”**中，单击**“确定”**。  
  
10. 保存 MFCAnimationWalkthroughView.cpp（它在编辑器中打开），但不要关闭它。  
  
### 向项目中添加动画对象  
  
1.  在解决方案资源管理器中，双击 MFCAnimationWalkthroughView.h 以打开它进行修改。  在紧接 `CMFCAnimationWalkthroughView` 类定义之前，添加以下代码来创建将处理与动画对象冲突的计划的自定义动画控制器。  
  
    ```  
    class CCustomAnimationController : public CAnimationController  
    {  
    public:  
        CCustomAnimationController()  
        {  
        }  
  
        virtual BOOL OnHasPriorityTrim(CAnimationGroup* pGroupScheduled, CAnimationGroup* pGroupNew, UI_ANIMATION_PRIORITY_EFFECT priorityEffect)  
        {  
            return TRUE;  
        }  
    };  
    ```  
  
2.  在 `CMFCAnimationWalkthroughView` 类的末尾，添加以下代码。  
  
    ```  
    CCustomAnimationController m_animationController;  
    CAnimationColor m_animationColor;   
    CAnimationRect m_animationRect;  
    ```  
  
3.  在 `DECLARE_MESSAGE_MAP()` 行之后，添加以下代码。  
  
    ```  
    void Animate(BOOL bDirection);  
    ```  
  
4.  保存文件并将其关闭。  
  
5.  在 MFCAnimationWalkthroughView.cpp 文件顶部的 `#include` 语句之后但任何类方法之前，添加以下代码。  
  
    ```  
    static int nAnimationGroup = 0;  
    static int nInfoAreaHeight = 40;  
    ```  
  
6.  在 `CMFCAnimationWalkthroughView` 的构造函数末尾，添加以下代码。  
  
    ```  
    m_animationController.EnableAnimationTimerEventHandler();  
    m_animationController.EnablePriorityComparisonHandler(UI_ANIMATION_PHT_TRIM);  
  
    m_animationColor = RGB(255, 255, 255);  
    m_animationRect = CRect(0, 0, 0, 0);  
  
    m_animationColor.SetID(-1, nAnimationGroup);  
    m_animationRect.SetID(-1, nAnimationGroup);  
  
    m_animationController.AddAnimationObject(&m_animationColor);  
    m_animationController.AddAnimationObject(&m_animationRect);  
    ```  
  
7.  找到 `CAnimationWalthroughView::PreCreateWindow` 方法，然后用以下代码替换它。  
  
    ```  
    BOOL CMFCAnimationWalkthroughView::PreCreateWindow(CREATESTRUCT& cs)  
    {  
        // TODO: Modify the Window class or styles here by modifying  
        //  the CREATESTRUCT cs  
  
        m_animationController.SetRelatedWnd(this);  
        return CView::PreCreateWindow(cs);  
    }  
    ```  
  
8.  找到 `CAnimationWalkthroughView::OnDraw` 方法，然后用以下代码替换它。  
  
    ```  
    void CMFCAnimationWalkthroughView::OnDraw(CDC* pDC)  
    {  
        CMFCAnimationWalkthroughDoc* pDoc = GetDocument();  
        ASSERT_VALID(pDoc);  
        if (!pDoc)  
            return;  
  
        // TODO: add draw code for native data here  
        CMemDC dcMem(*pDC, this);  
        CDC& dc = dcMem.GetDC();  
  
        CRect rect;  
        GetClientRect(rect);  
  
        dc.FillSolidRect(rect, GetSysColor(COLOR_WINDOW));  
  
        CString strRGB;  
        strRGB.Format(_T("Fill Color is: %d; %d; %d"), GetRValue(m_animationColor), GetGValue(m_animationColor), GetBValue(m_animationColor));  
  
        dc.DrawText(strRGB, rect, DT_CENTER);  
        rect.top += nInfoAreaHeight;  
  
        CBrush br;  
  
        br.CreateSolidBrush(m_animationColor);  
        CBrush* pBrushOld = dc.SelectObject(&br);  
  
        dc.Rectangle((CRect)m_animationRect);  
        dc.SelectObject(pBrushOld);  
    }  
    ```  
  
9. 在文件末尾添加以下代码。  
  
    ```  
    void CMFCAnimationWalkthroughView::Animate(BOOL bDirection)  
    {  
        static UI_ANIMATION_SECONDS duration = 3;  
        static DOUBLE dblSpeed = 35.;  
        static BYTE nStartColor = 50;  
        static BYTE nEndColor = 255;  
  
        BYTE nRedColorFinal = bDirection ? nStartColor : nEndColor;  
        BYTE nGreenColorFinal = bDirection ? nStartColor : nEndColor;  
        BYTE nBlueColorFinal = bDirection ? nStartColor : nEndColor;  
  
        CLinearTransition* pRedTransition = new CLinearTransition(duration, (DOUBLE)nRedColorFinal);  
        CSmoothStopTransition* pGreenTransition = new CSmoothStopTransition(duration, (DOUBLE)nGreenColorFinal);  
        CLinearTransitionFromSpeed* pBlueTransition = new CLinearTransitionFromSpeed(dblSpeed, (DOUBLE)nBlueColorFinal);  
  
        m_animationColor.AddTransition(pRedTransition, pGreenTransition, pBlueTransition);  
  
        CRect rectClient;  
        GetClientRect(rectClient);  
        rectClient.top += nInfoAreaHeight;  
  
        int nLeftFinal = bDirection ? rectClient.left : rectClient.CenterPoint().x;  
        int nTopFinal = bDirection ? rectClient.top : rectClient.CenterPoint().y;  
        int nRightFinal = bDirection ? rectClient.right : rectClient.CenterPoint().x;  
        int nBottomFinal = bDirection ? rectClient.bottom : rectClient.CenterPoint().y;  
  
        CLinearTransition* pLeftTransition = new CLinearTransition(duration, nLeftFinal);  
        CLinearTransition* pTopTransition = new CLinearTransition(duration, nTopFinal);  
        CLinearTransition* pRightTransition = new CLinearTransition(duration, nRightFinal);  
        CLinearTransition* pBottomTransition = new CLinearTransition(duration, nBottomFinal);  
  
        m_animationRect.AddTransition(pLeftTransition, pTopTransition, pRightTransition, pBottomTransition);  
  
        CBaseKeyFrame* pKeyframeStart = CAnimationController::GetKeyframeStoryboardStart();  
        CKeyFrame* pKeyFrameEnd = m_animationController.CreateKeyframe(nAnimationGroup, pBlueTransition);  
  
        pLeftTransition->SetKeyframes(pKeyframeStart, pKeyFrameEnd);  
        pTopTransition->SetKeyframes(pKeyframeStart, pKeyFrameEnd);  
        pRightTransition->SetKeyframes(pKeyframeStart, pKeyFrameEnd);  
        pBottomTransition->SetKeyframes(pKeyframeStart, pKeyFrameEnd);  
  
        m_animationController.AnimateGroup(nAnimationGroup);  
    }  
    ```  
  
10. 在**“项目”**菜单上单击**“类向导”**。  
  
11. 在**“MFC 类向导”**中的**“类名”**下，选择 `CMFCAnimationWalkthroughView`。  
  
12. 在**“消息”**选项卡上的**“消息”**框中，选择 `WM_ERASEBKGND`，单击**“添加处理程序”**，然后单击**“确定”**。  
  
13. 在 MFCAnimationWalkthroughView.cpp 中，用以下代码替换 `OnEraseBkgnd` 的实现以减少重新绘制动画对象时其中的闪烁次数。  
  
    ```  
    BOOL CMFCAnimationWalkthroughView::OnEraseBkgnd(CDC* /*pDC*/)  
    {  
        return TRUE;  
    }  
    ```  
  
14. 用以下代码替换 `CMFCAnimationWalkthroughView::OnAnimationStartforward`、`CMFCAnimationWalkthroughView::OnAnimationStartbackward` 和 `CMFCAnimationWalkthroughView::OnAnimationStop` 的实现。  
  
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
  
15. 保存文件并将其关闭。  
  
### 使动画对象在窗口中居中  
  
1.  在**“解决方案资源管理器”**中，双击 MFCAnimationWalkthroughView.h 以打开它进行修改。  在 `CMFCAnimationWalkthroughView` 类的末尾，紧接 `m_animationRect` 的定义之后，添加以下代码。  
  
    ```  
    BOOL m_bCurrentDirection;  
    ```  
  
2.  保存文件并将其关闭。  
  
3.  在**“项目”**菜单上单击**“类向导”**。  
  
4.  在**“MFC 类向导”**中的**“类名”**下，选择 `CMFCAnimationWalkthroughView`。  
  
5.  在**“消息”**选项卡上的**“消息”**框中，选择 `WM_SIZE`，单击**“添加处理程序”**，然后单击**“确定”**。  
  
6.  在 MFCAnimationWalkthroughView.cpp 中，用以下代码替换 `CMFCAnimationWalkthroughView::OnSize` 的代码。  
  
    ```  
    void CMFCAnimationWalkthroughView::OnSize(UINT nType, int cx, int cy)  
    {  
        CView::OnSize(nType, cx, cy);  
  
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
  
7.  在 `CMFCAnimationWalkthroughView` 的构造函数开头，添加以下代码。  
  
    ```  
    m_bCurrentDirection = TRUE;  
    ```  
  
8.  在 `CMFCAnimationWalkthroughView::Animate` 方法开头，添加以下代码。  
  
    ```  
    m_bCurrentDirection = bDirection;  
    ```  
  
9. 保存文件并将其关闭。  
  
### 验证结果  
  
1.  生成并运行应用程序。  在**“Animation”（动画）**菜单上，单击**“Start Forward”（开始前进）**。  应显示一个矩形，然后填充中央区域。  当您单击**“Start Backward”（开始后退）**时，动画应倒退；当您单击**“Stop”（停止）**时，它应停止。  矩形的填充颜色应随着动画的进行而更改，并且当前颜色应显示在动画窗口顶部。  
  
## 请参阅  
 [演练](../mfc/walkthroughs-mfc.md)