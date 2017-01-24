---
title: "演练：向 MFC 项目添加 D2D 对象 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "D2D [MFC]"
  - "MFC, D2D"
ms.assetid: dda36c33-c231-4da6-a62f-72d69a12b6dd
caps.latest.revision: 20
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 演练：向 MFC 项目添加 D2D 对象
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此演练介绍如何将基本 Direct2D \(D2D\) 对象添加到 Visual C\+\+ Microsoft 基础类库 \(MFC\) 项目中，然后将该项目构建到在渐变背景上输出“Hello, world”的应用程序中。  
  
 此演练演示如何完成以下这些任务：  
  
-   创建 MFC 应用程序。  
  
-   创建一个纯色画笔和一个线性渐变画笔。  
  
-   修改渐变画笔，以便在调整窗口大小时它会相应更改。  
  
-   实现 D2D 绘图处理程序。  
  
-   验证结果。  
  
 [!INCLUDE[note_settings_general](../mfc/includes/note_settings_general_md.md)]  
  
## 系统必备  
 若要完成本演练，需要 Visual Studio。  
  
### 创建 MFC 应用程序  
  
1.  在**“文件”**菜单上指向**“新建”**，然后单击**“项目”**。  
  
2.  在**“新建项目”**对话框左窗格的**“已安装的模板”**下，展开**“Visual C\+\+”**，然后选择**“MFC”**。  在中间窗格中，选择**“MFC 应用程序”**。  在**“名称”**框中键入 `MFCD2DWalkthrough`。  单击**“确定”**。  
  
3.  在**“MFC 应用程序向导”**中，单击**“完成”**而不更改任何设置。  
  
### 创建一个纯色画笔和一个线性渐变画笔  
  
1.  在**“解决方案资源管理器”**中的**“MFCD2DWalkthrough”**项目的**“头文件”**文件夹中，打开 MFCD2DWalkthroughView.h。  将以下代码添加到 `CMFCD2DWalkthroughView` 类以创建三个数据变量。  
  
    ```  
    CD2DTextFormat* m_pTextFormat;  
    CD2DSolidColorBrush* m_pBlackBrush;  
    CD2DLinearGradientBrush* m_pLinearGradientBrush;  
    ```  
  
     保存文件并将其关闭。  
  
2.  在**“源文件”**文件夹中，打开 MFCD2DWalkthroughView.cpp。  在 `CMFCD2DWalkthroughView` 类的构造函数中，添加以下代码。  
  
    ```  
    // Enable D2D support for this window:  
    EnableD2DSupport();  
  
    // Initialize D2D resources:  
    m_pBlackBrush = new CD2DSolidColorBrush(GetRenderTarget(), D2D1::ColorF(D2D1::ColorF::Black));  
  
    m_pTextFormat = new CD2DTextFormat(GetRenderTarget(), _T("Verdana"), 50);  
    m_pTextFormat->Get()->SetTextAlignment(DWRITE_TEXT_ALIGNMENT_CENTER);  
    m_pTextFormat->Get()->SetParagraphAlignment(DWRITE_PARAGRAPH_ALIGNMENT_CENTER);  
  
    D2D1_GRADIENT_STOP gradientStops[2];  
  
    gradientStops[0].color = D2D1::ColorF(D2D1::ColorF::White);  
    gradientStops[0].position = 0.f;  
    gradientStops[1].color = D2D1::ColorF(D2D1::ColorF::Indigo);  
    gradientStops[1].position = 1.f;  
  
    m_pLinearGradientBrush = new CD2DLinearGradientBrush(GetRenderTarget(),   
        gradientStops, ARRAYSIZE(gradientStops),  
        D2D1::LinearGradientBrushProperties(D2D1::Point2F(0, 0), D2D1::Point2F(0, 0)));  
    ```  
  
     保存文件并将其关闭。  
  
### 修改渐变画笔，以便在调整窗口大小时它会相应更改  
  
1.  在**“项目”**菜单上单击**“类向导”**。  
  
2.  在**“MFC 类向导”**中的**“类名”**下，选择 `CMFCD2DWalkthroughView`。  
  
3.  在**“消息”**选项卡上的**“消息”**框中，选择 `WM_SIZE`，然后单击**“添加处理程序”**。  此操作将 `OnSize` 消息处理程序添加到 `CMFCD2DWalkthroughView` 类。  
  
4.  在**“现有处理程序”**框中，选择 `OnSize`。  单击**“编辑代码”**以显示 `CMFCD2DWalkthroughView::OnSize` 方法。  在此方法的末尾，添加以下代码。  
  
    ```  
    m_pLinearGradientBrush->SetEndPoint(CPoint(cx, cy));  
    ```  
  
     保存文件并将其关闭。  
  
### 实现 D2D 绘图处理程序  
  
1.  在**“项目”**菜单上单击**“类向导”**。  
  
2.  在**“MFC 类向导”**中的**“类名”**下，选择 `CMFCD2DWalkthroughView`。  
  
3.  在**“消息”**选项卡上，单击**“添加自定义消息”**。  
  
4.  在**“添加自定义消息”**对话框的**“自定义 Windows 消息”**框中，键入 `AFX_WM_DRAW2D`。  在**“消息处理程序名称”**框中，键入 `OnDraw2D`。  选择**“已注册的消息”**选项，然后单击**“确定”**。  此操作将 `AFX_WM_DRAW2D` 消息的消息处理程序添加到 `CMFCD2DWalkthroughView` 类。  
  
5.  在**“现有处理程序”**框中，选择 `OnDraw2D`。  单击**“编辑代码”**以显示 `CMFCD2DWalkthroughView::OnDraw2D` 方法。  对 `CMFCD2DWalkthroughView::OnDrawD2D` 方法使用以下代码。  
  
    ```  
    afx_msg LRESULT CMFCD2DWalkthroughView::OnDraw2D(WPARAM wParam, LPARAM lParam)  
    {  
        CHwndRenderTarget* pRenderTarget = (CHwndRenderTarget*)lParam;  
        ASSERT_VALID(pRenderTarget);  
  
        CRect rect;  
        GetClientRect(rect);  
  
        pRenderTarget->FillRectangle(rect, m_pLinearGradientBrush);  
        pRenderTarget->DrawText(_T("Hello, World!"), rect, m_pBlackBrush, m_pTextFormat);  
  
        return TRUE;  
    }  
    ```  
  
     保存文件并将其关闭。  
  
### 验证结果  
  
1.  生成并运行应用程序。  它应有一个在您调整窗口大小时更改的渐变矩形。“Hello World\!”应显示在矩形中央。  
  
## 请参阅  
 [演练](../mfc/walkthroughs-mfc.md)