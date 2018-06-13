---
title: 演练： 向 MFC 项目添加 D2D 对象 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC, D2D
- D2D [MFC]
ms.assetid: dda36c33-c231-4da6-a62f-72d69a12b6dd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7985b36c0eeaa7adf5441a7a6fbb3314bac8353f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33384015"
---
# <a name="walkthrough-adding-a-d2d-object-to-an-mfc-project"></a>演练：向 MFC 项目添加 D2D 对象
本演练介绍如何添加基本 Direct2D (D2D) 到 Visual c + +，Microsoft 基础类库 (MFC) 项目对象，然后将该项目生成的应用程序将打印为"Hello，world"渐变背景上。  
  
 本演练演示如何完成这些任务：  
  
-   创建 MFC 应用程序。  
  
-   创建纯色画笔和线性渐变画笔。  
  
-   因此，它将更改相应地调整窗口大小时，请修改渐变画笔。  
  
-   实现 D2D 绘制处理程序。  
  
-   验证结果。  
  
 [!INCLUDE[note_settings_general](../mfc/includes/note_settings_general_md.md)]  
  
## <a name="prerequisites"></a>系统必备  
 若要完成本演练，您必须具有 Visual Studio。  
  
### <a name="to-create-an-mfc-application"></a>若要创建 MFC 应用程序  
  
1.  在 **“文件”** 菜单上指向 **“新建”** ，然后单击 **“项目”**。  
  
2.  在**新项目**对话框中，在左窗格中下**已安装的模板**，展开**Visual c + +** ，然后选择**MFC**。 在中间窗格中，选择**MFC 应用程序**。 在“名称”框中键入 `MFCD2DWalkthrough`。 单击 **“确定”**。  
  
3.  在**MFC 应用程序向导**，单击**完成**而无需更改任何设置。  
  
### <a name="to-create-a-solid-color-brush-and-a-linear-gradient-brush"></a>若要创建纯色画笔和线性渐变画笔  
  
1.  在**解决方案资源管理器**中**MFCD2DWalkthrough**项目，在**标头文件**文件夹中，打开 MFCD2DWalkthroughView.h。 以下代码添加到`CMFCD2DWalkthroughView`类来创建三个数据变量。  
  
 ```  
    CD2DTextFormat* m_pTextFormat;  
    CD2DSolidColorBrush* m_pBlackBrush;  
    CD2DLinearGradientBrush* m_pLinearGradientBrush;  
 ```  
  
     保存该文件并将其关闭。  
  
2.  在**源文件**文件夹中，打开 MFCD2DWalkthroughView.cpp。 构造函数中`CMFCD2DWalkthroughView`类中，添加下面的代码。  
  
 ' * / / 启用对此窗口 D2D 支持：  
    EnableD2DSupport();

 * / 初始化 D2D 资源：  
    m_pBlackBrush = 新 CD2DSolidColorBrush(GetRenderTarget()，D2D1::ColorF(D2D1::ColorF::Black));

 
    m_pTextFormat = 新 CD2DTextFormat(GetRenderTarget()，_T("Verdana")，50);

    m_pTextFormat-> get （)-> SetTextAlignment(DWRITE_TEXT_ALIGNMENT_CENTER);

 m_pTextFormat-> get （)-> SetParagraphAlignment(DWRITE_PARAGRAPH_ALIGNMENT_CENTER);

 
    D2D1_GRADIENT_STOP gradientStops [2];  
 
    gradientStops [0].color = D2D1::ColorF(D2D1::ColorF::White);

    gradientStops [0].position = 0.f;  
    gradientStops [1].color = D2D1::ColorF(D2D1::ColorF::Indigo);

    gradientStops [1].position = 1.f;  
 
    m_pLinearGradientBrush = 新 CD2DLinearGradientBrush(GetRenderTarget()   
    gradientStops，ARRAYSIZE(gradientStops)，  
    D2D1::LinearGradientBrushProperties （D2D1::Point2F （0，0），D2D1::Point2F （0，0））);

 ```  
  
     Save the file and close it.  
  
### To modify the gradient brush so that it will change appropriately when the window is resized  
  
1.  On the **Project** menu, click **Class Wizard**.  
  
2.  In the **MFC Class Wizard**, under **Class name**, select `CMFCD2DWalkthroughView`.  
  
3.  On the **Messages** tab, in the **Messages** box, select `WM_SIZE` and then click **Add Handler**. This action adds the `OnSize` message handler to the `CMFCD2DWalkthroughView` class.  
  
4.  In the **Existing handlers** box, select `OnSize`. Click **Edit Code** to display the `CMFCD2DWalkthroughView::OnSize` method. At the end of the method, add the following code.  
  
 ```  
    m_pLinearGradientBrush-> SetEndPoint (CPoint （cx，cy）);

 ```  
  
     Save the file and close it.  
  
### To implement a D2D drawing handler  
  
1.  On the **Project** menu, click **Class Wizard**.  
  
2.  In the **MFC Class Wizard**, under **Class name**, select `CMFCD2DWalkthroughView`.  
  
3.  On the **Messages** tab, click **Add Custom Message**.  
  
4.  In the **Add Custom Message** dialog box, in the **Custom Windows Message** box, type `AFX_WM_DRAW2D`. In the **Message handler name** box, type `OnDraw2D`. Select the **Registered Message** option and then click **OK**. This action adds a message handler for the `AFX_WM_DRAW2D` message to the `CMFCD2DWalkthroughView` class.  
  
5.  In the **Existing handlers** box, select `OnDraw2D`. Click **Edit Code** to display the `CMFCD2DWalkthroughView::OnDraw2D` method. Use the following code for the `CMFCD2DWalkthroughView::OnDrawD2D` method.  
  
 ```  
    afx_msg LRESULT CMFCD2DWalkthroughView::OnDraw2D(WPARAM wParam, LPARAM lParam)  
    {  
 CHwndRenderTarget * pRenderTarget = （CHwndRenderTarget *） lParam;  
    ASSERT_VALID(pRenderTarget);

 
    CRect rect;  
    GetClientRect(rect);

 
    pRenderTarget-> FillRectangle （rect，m_pLinearGradientBrush）;

    pRenderTarget-> DrawText （_T （"Hello，World ！"），rect、 m_pBlackBrush、 m_pTextFormat）;

 
    返回 TRUE;  
 }  
 ```  
  
     Save the file and close it.  
  
### To verify the results  
  
1.  Build and run the application. It should have a gradient rectangle that changes when you resize the window. “Hello World!” should be displayed in the center of the rectangle.  
  
## See Also  
 [Walkthroughs](../mfc/walkthroughs-mfc.md)

