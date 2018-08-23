---
title: 演练： 向 MFC 项目添加 D2D 对象 |Microsoft 文档
ms.custom: ''
ms.date: 06/19/2018
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
ms.openlocfilehash: 87e1c696f3da374d7b71e1b24e3a8bd3ebfe41b9
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/26/2018
ms.locfileid: "36954866"
---
# <a name="walkthrough-adding-a-d2d-object-to-an-mfc-project"></a>演练：向 MFC 项目添加 D2D 对象

本演练介绍如何添加基本 Direct2D (D2D) 到 Visual c + +，Microsoft 基础类库 (MFC) 项目对象，然后将该项目生成的应用程序将打印为"Hello，world"渐变背景上。

本演练演示如何完成这些任务：

- 创建 MFC 应用程序。

- 创建纯色画笔和线性渐变画笔。

- 因此，它将更改相应地调整窗口大小时，请修改渐变画笔。

- 实现 D2D 绘制处理程序。

- 验证结果。

[!INCLUDE[note_settings_general](../mfc/includes/note_settings_general_md.md)]

## <a name="prerequisites"></a>系统必备

若要完成本演练，你必须使用安装的 Visual Studio**使用 c + + 桌面开发**工作负荷和可选**为 x86 和 x64 的 Visual c + + MFC**组件。

## <a name="to-create-an-mfc-application"></a>若要创建 MFC 应用程序

1. 上**文件**菜单上，指向**新建**，然后选择**项目**。

2. 在**新项目**对话框中，在左窗格中下**已安装的模板**，展开**Visual c + +** ，然后选择**MFC**。 在中间窗格中，选择**MFC 应用程序**。 在**名称**框中，键入*MFCD2DWalkthrough*。 选择 **“确定”**。

3. 在**MFC 应用程序向导**，选择**完成**而无需更改任何设置。

## <a name="to-create-a-solid-color-brush-and-a-linear-gradient-brush"></a>若要创建纯色画笔和线性渐变画笔

1. 在**解决方案资源管理器**中**MFCD2DWalkthrough**项目，在**标头文件**文件夹中，打开 MFCD2DWalkthroughView.h。 添加此代码与`CMFCD2DWalkthroughView`类来创建三个数据变量：

   ```cpp
   CD2DTextFormat* m_pTextFormat;
   CD2DSolidColorBrush* m_pBlackBrush;
   CD2DLinearGradientBrush* m_pLinearGradientBrush;
   ```

   保存该文件并将其关闭。

2. 在**源文件**文件夹中，打开 MFCD2DWalkthroughView.cpp。 构造函数中`CMFCD2DWalkthroughView`类中，添加此代码：

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

## <a name="to-modify-the-gradient-brush-so-that-it-will-change-appropriately-when-the-window-is-resized"></a>若要修改渐变画笔，以便它将会更改相应地调整窗口大小时

1. 上**项目**菜单上，选择**类向导**。

2. 在**MFC 类向导**下**类名**，选择`CMFCD2DWalkthroughView`。

3. 上**消息**选项卡上，在**消息**框中，选择`WM_SIZE`，然后选择**添加处理程序**。 此操作将添加`OnSize`消息处理程序`CMFCD2DWalkthroughView`类。

4. 在**现有处理程序**框中，选择`OnSize`。 选择**编辑代码**以显示`CMFCD2DWalkthroughView::OnSize`方法。 在该方法的末尾，添加以下代码。

   ```cpp
   m_pLinearGradientBrush->SetEndPoint(CPoint(cx, cy));
   ```

   保存该文件并将其关闭。

## <a name="to-implement-a-d2d-drawing-handler"></a>若要实现 D2D 绘制处理程序

1. 上**项目**菜单上，选择**类向导**。

2. 在**MFC 类向导**下**类名**，选择`CMFCD2DWalkthroughView`。

3. 上**消息**选项卡上，选择**添加自定义消息**。

4. 在**添加自定义消息**对话框中，在**自定义 Windows 消息**框中，键入*AFX_WM_DRAW2D*。 在**消息处理程序名称**框中，键入*OnDraw2D*。 选择**注册消息**选项，然后选择**确定**。 此操作将添加到 AFX_WM_DRAW2D 消息的消息处理`CMFCD2DWalkthroughView`类。

5. 在**现有处理程序**框中，选择`OnDraw2D`。 选择**编辑代码**以显示`CMFCD2DWalkthroughView::OnDraw2D`方法。 使用这段代码用于`CMFCD2DWalkthroughView::OnDrawD2D`方法：

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

## <a name="to-verify-the-results"></a>若要验证的结果

- 生成并运行应用程序。 它应具有渐变矩形时重设窗口大小更改。 "Hello World ！" 应显示在中心的矩形中。

## <a name="see-also"></a>请参阅

- [演练](../mfc/walkthroughs-mfc.md)
