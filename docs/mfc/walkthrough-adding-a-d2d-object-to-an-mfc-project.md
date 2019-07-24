---
title: 演练：向 MFC 项目添加 D2D 对象
ms.date: 04/25/2019
helpviewer_keywords:
- MFC, D2D
- D2D [MFC]
ms.assetid: dda36c33-c231-4da6-a62f-72d69a12b6dd
ms.openlocfilehash: cbb9e4002bb47ad8f65678c7a324267ca9717e94
ms.sourcegitcommit: f82a6de52470070accb09a3a8f8b08060c492efa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2019
ms.locfileid: "68411752"
---
# <a name="walkthrough-adding-a-d2d-object-to-an-mfc-project"></a>演练：向 MFC 项目添加 D2D 对象

本演练介绍如何将基本 Direct2D (D2D) 对象添加到视觉C++对象 MICROSOFT 基础类库 (MFC) 项目, 然后将该项目生成到打印 "Hello, World!" 的应用程序中 在渐变背景上。

本演练演示如何完成以下任务:

- 创建 MFC 应用程序。

- 创建纯色画笔和线性渐变画笔。

- 修改渐变画笔, 使其在调整窗口大小时能相应地更改。

- 实现 D2D 绘图处理程序。

- 验证结果。

[!INCLUDE[note_settings_general](../mfc/includes/note_settings_general_md.md)]

## <a name="prerequisites"></a>系统必备

若要完成本演练, 您必须在安装了 visual Studio 时使用工作负载的**桌面开发C++** 以及**适用于 x86 和 x64 组件的可选 Visual C++ MFC** 。

## <a name="to-create-an-mfc-application"></a>创建 MFC 应用程序

1. 使用**Mfc 应用程序向导**创建 MFC 应用程序。 请参阅[演练：使用新的 MFC Shell 控件](walkthrough-using-the-new-mfc-shell-controls.md)获取有关如何为你的 Visual Studio 版本打开向导的说明。

1. 在 "**名称**" 框中, 键入*MFCD2DWalkthrough*。 选择 **“确定”** 。

1. 在**MFC 应用程序向导**中, 选择 "**完成**" 而不更改任何设置。

## <a name="to-create-a-solid-color-brush-and-a-linear-gradient-brush"></a>创建纯色画笔和线性渐变画笔

1. 在**解决方案资源管理器**的 " **MFCD2DWalkthrough** " 项目的 "**头文件**" 文件夹中, 打开 MFCD2DWalkthroughView。 将此代码添加到`CMFCD2DWalkthroughView`类, 以创建三个数据变量:

   ```cpp
   CD2DTextFormat* m_pTextFormat;
   CD2DSolidColorBrush* m_pBlackBrush;
   CD2DLinearGradientBrush* m_pLinearGradientBrush;
   ```

   保存该文件并将其关闭。

1. 在 "**源文件**" 文件夹中, 打开 MFCD2DWalkthroughView。 在`CMFCD2DWalkthroughView`类的构造函数中, 添加以下代码:

   ```cpp
   // Enable D2D support for this window:
   EnableD2DSupport();

   // Initialize D2D resources:
   m_pBlackBrush = new CD2DSolidColorBrush(
       GetRenderTarget(),
       D2D1::ColorF(D2D1::ColorF::Black));

   m_pTextFormat = new CD2DTextFormat(
       GetRenderTarget(),
       _T("Verdana"),
       50);

   m_pTextFormat->Get()->SetTextAlignment(
       DWRITE_TEXT_ALIGNMENT_CENTER);

   m_pTextFormat->Get()->SetParagraphAlignment(
       DWRITE_PARAGRAPH_ALIGNMENT_CENTER);

   D2D1_GRADIENT_STOP gradientStops[2];

   gradientStops[0].color =
       D2D1::ColorF(D2D1::ColorF::White);

   gradientStops[0].position = 0.f;
   gradientStops[1].color =
       D2D1::ColorF(D2D1::ColorF::Indigo);

   gradientStops[1].position = 1.f;

   m_pLinearGradientBrush = new CD2DLinearGradientBrush(
       GetRenderTarget(),
       gradientStops,
       ARRAYSIZE(gradientStops),
       D2D1::LinearGradientBrushProperties(
           D2D1::Point2F(0,0),
           D2D1::Point2F(0,0)));
   ```

   保存该文件并将其关闭。

## <a name="to-modify-the-gradient-brush-so-that-it-will-change-appropriately-when-the-window-is-resized"></a>修改渐变画笔, 使其在调整窗口大小时进行适当的更改

1. 在 "**项目**" 菜单上, 选择 "**类向导**"。

1. 在**MFC 类向导**的 "**类名称**" 下, `CMFCD2DWalkthroughView`选择。

1. 在 "**消息**" 选项卡上的 "**消息**" `WM_SIZE`框中, 选择, 然后选择 "**添加处理程序**"。 此操作向`CMFCD2DWalkthroughView`类`OnSize`添加消息处理程序。

1. 在 "**现有处理程序**" 框`OnSize`中, 选择。 选择 "**编辑代码**" `CMFCD2DWalkthroughView::OnSize`以显示方法。 在方法的末尾, 添加以下代码。

   ```cpp
   m_pLinearGradientBrush->SetEndPoint(CPoint(cx, cy));
   ```

   保存该文件并将其关闭。

## <a name="to-implement-a-d2d-drawing-handler"></a>实现 D2D 绘图处理程序

1. 在 "**项目**" 菜单上, 选择 "**类向导**"。

1. 在**MFC 类向导**的 "**类名称**" 下, `CMFCD2DWalkthroughView`选择。

1. 在 "**消息**" 选项卡上, 选择 "**添加自定义消息**"。

1. 在 "**添加自定义消息**" 对话框的 "**自定义 Windows 消息**" 框中, 键入 " *AFX_WM_DRAW2D*"。 在 "**消息处理程序名称**" 框中, 键入*OnDraw2D*。 选择 "**已注册的消息**" 选项, 然后选择 **"确定"** 。 此操作向`CMFCD2DWalkthroughView`类添加 AFX_WM_DRAW2D 消息的消息处理程序。

1. 在 "**现有处理程序**" 框`OnDraw2D`中, 选择。 选择 "**编辑代码**" `CMFCD2DWalkthroughView::OnDraw2D`以显示方法。 将此代码`CMFCD2DWalkthroughView::OnDrawD2D`用于方法:

   ```cpp
   afx_msg LRESULT CMFCD2DWalkthroughView::OnDraw2D(
       WPARAM wParam,
       LPARAM lParam)
   {
       CHwndRenderTarget* pRenderTarget = (CHwndRenderTarget*)lParam;
       ASSERT_VALID(pRenderTarget);

       CRect rect;
       GetClientRect(rect);

       pRenderTarget->FillRectangle(rect, m_pLinearGradientBrush);

       pRenderTarget->DrawText(
           _T("Hello, World!"),
           rect,
           m_pBlackBrush,
           m_pTextFormat);

       return TRUE;
   }
   ```

   保存该文件并将其关闭。

## <a name="to-verify-the-results"></a>验证结果

生成并运行应用程序。 在调整窗口大小时, 它应具有一个变化的渐变矩形。 "Hello World!" 应显示在矩形的中心。

## <a name="see-also"></a>请参阅

[演练](../mfc/walkthroughs-mfc.md)
