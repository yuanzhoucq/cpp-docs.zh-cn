---
title: "动态布局 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 8598cfb2-c8d4-4f5a-bf2b-59dc4653e042
caps.latest.revision: 7
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 动态布局
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用 [!INCLUDE[vs_dev14](../ide/includes/vs_dev14_md.md)] 中的 MFC，可创建用户可以调整大小的对话框，并可以控制调整布局以更改大小的方式。  例如，可以将对话框底部的按钮附加到下边缘，使其始终保持在底部。  还可以将某些控件（如列表框、编辑框和文本字段）设置为在用户展开对话框时展开。  
  
## 为 MFC 对话框指定动态布局设置  
 当用户调整对话框大小时，该对话框中的控件可以调整大小，或沿 X 和 Y 方向移动。  用户重新调整对话框大小时控件大小或位置的更改称为动态布局。  例如，以下是调整大小之前的对话框：  
  
 ![调整大小前的对话框。](../mfc/media/mfcdynamiclayout4.png "MFCDynamicLayout4")  
  
 调整大小后，列表框区域会增大，以显示更多项，并且以下按钮将沿右下角移动：  
  
 ![调整大小后的对话框。](../mfc/media/mfcdynamiclayout5.png "MFCDynamicLayout5")  
  
 可以通过在 IDE 的资源编辑器中对每个控件指定详细信息来控制动态布局，也可以通过访问特定控件的 CMFCDynamicLayout 对象并设置其属性以编程方式执行操作。  
  
### 在资源编辑器中设置动态布局属性  
 可以使用资源编辑器设置对话框的动态布局行为，而无需编写任何代码。  
  
##### 在资源编辑器中设置动态布局属性  
  
1.  打开一个 MFC 项目，打开想要在对话框编辑器中使用的对话框。  
  
     ![在资源编辑器中打开对话框。](../mfc/media/mfcdynamiclayout3.png "MFCDynamicLayout3")  
  
2.  选择一个控件，然后在属性窗口中，设置其动态布局属性。  属性窗口中的**“动态布局”**部分包含**“移动类型”**和**“调整大小类型”**属性，具体取决于针对这些属性选择的值，这些特定属性定义控件的移动和大小更改程度。  **“移动类型”**确定对话框的大小发生更改时控件如何移动；**“调整大小类型”**确定对话框的大小发生更改时控件的大小如何调整。  **“移动类型”**和**“调整大小类型”**可能是**“水平”**、**“垂直”**、**“两者”**或**“无”**，具体取决于想要动态更改的维度。  水平是 X 维度；垂直是 Y 方向。  
  
3.  如果想要使按钮等控件的大小固定不变并保持位于右下角（就像很常见的**“确定”**或**“取消”**按钮一样），请将**“调整大小类型”**设置为**“无”**，将**“移动类型”**设置为**“两者”**。  对于**“移动类型”**下的**“移动 X”**和**“移动 Y”**值，设置为 100% 可使控件与右下角保持固定的距离。  
  
     ![动态布局](../mfc/media/mfcdynamiclayout1.png "MFCDynamicLayout1")  
  
4.  假设你还有一个希望在对话框展开时展开的控件。  通常情况下，用户可能会展开对话框，以展开多行编辑框，从而增加文本区域的大小，他们也可能会展开列表控件，以查看更多的数据。  对于这种情况，请将**“调整大小类型”**设置为“两者”，将**“移动类型”**设置为“无”。  然后，将**“调整大小 X”** 和**“调整大小 Y”** 设置为 100。  
  
     ![动态布局设置](../mfc/media/mfcdynamiclayout2.png "MFCDynamicLayout2")  
  
5.  使用可能对你的控件有意义的其他值进行试验。  例如，具有单行文本框的对话框可能将**“调整大小类型”**设置为**“水平”**。  
  
### 以编程方式设置动态布局属性  
 之前的过程适用于在设计时为对话框指定动态布局属性，但如果希望在运行时控制动态布局，则可以采用编程方式设置动态布局属性。  
  
##### 以编程方式设置动态布局属性  
  
1.  在自己对话框类的实现代码中查找或创建一个想要为该对话指定动态布局的位置。  例如，你可能希望在对话框中添加一个方法（如 `AdjustLayout`），并从不要更改布局的位置进行调用。  你可能会首先从构造函数中调用，也可能在对对话框进行更改之后调用。  
  
2.  对于对话框，请调用 CWnd 类的方法 [GetDynamicLayout](../Topic/CWnd::GetDynamicLayout.md)。  GetDynamicLayout 返回了指向 CMFCDynamicLayout 对象的指针。  
  
    ```  
    CMFCDynamicLayout* dynamicLayout = pDialog->GetDynamicLayout();  
    ```  
  
3.  对于希望向其添加动态行为的第一个控件，请在动态布局类上使用静态方法，以创建对控件的调整方式进行编码的 [MoveSettings](../Topic/CMFCDynamicLayout::MoveSettings%20Structure.md) 结构。  通过首先选择适当的静态方法来执行此操作：[CMFCDynamicLayout::MoveHorizontal](../Topic/CMFCDynamicLayout::MoveHorizontal.md)、[CMFCDynamicLayout::MoveVertical](../Topic/CMFCDynamicLayout::MoveVertical.md)、[CMFCDynamicLayout::MoveNone](../Topic/CMFCDynamicLayout::MoveNone.md) 或 [CMFCDynamicLayout::MoveHorizontalAndVertical](../Topic/CMFCDynamicLayout::MoveHorizontalAndVertical.md)。  对移动的水平和\/或垂直特性传入一个百分比。  这些静态方法都将返回新创建的 MoveSettings 对象，你可以使用该对象来指定控件的移动行为。  
  
     记住，100 表示完全根据该对话框更改的大小进行移动，这会导致控件的边缘与新边框保持固定的距离。  
  
    ```  
    MoveSettings moveSettings = CMFCDynamicLayout::MoveHorizontal(100);  
    ```  
  
4.  对使用 [SizeSettings](../Topic/CMFCDynamicLayout::SizeSettings%20Structure.md) 类型的大小行为执行相同的操作。  例如，若要指定当对话框调整大小时控件不会更改大小，请使用以下代码：  
  
    ```  
    SizeSettings sizeSettings = CMFCDynamicLayout::SizeNone();  
    ```  
  
5.  使用 [CMFCDynamicLayout::AddItem](../Topic/CMFCDynamicLayout::AddItem.md) 方法将控件添加到动态布局管理器。  指定所需控件的不同方法有两种重载。  一种重载使用控件的窗口句柄 \(HWND\)，另一种使用控件 ID。  
  
    ```  
    dynamicLayout->AddItem(hWndControl, moveSettings, sizeSettings);  
    ```  
  
6.  对每个需要移动或调整大小的控件进行重复。  
  
7.  如有必要，可以使用 [CMFCDynamicLayout::HasItem](../Topic/CMFCDynamicLayout::HasItem.md) 方法确定控件是否已在经过动态布局更改的控件列表上，或者使用 [CMFCDynamicLayout::IsEmpty](../Topic/CMFCDynamicLayout::IsEmpty.md) 方法确定是否存在任何可能发生更改的控件。  
  
8.  若要启用对话框布局，请调用 [CWnd::EnableDynamicLayout](../Topic/CWnd::EnableDynamicLayout.md) 方法。  
  
    ```  
    pDialog->EnableDynamicLayout(TRUE);  
    ```  
  
9. 用户下次调整对话框大小时，将调用实际应用设置的[CMFCDynamicLayout::Adjust](../Topic/CMFCDynamicLayout::Adjust.md) 方法。  
  
10. 若要禁用动态布局，请调用 `bEnabled` 参数为 `FALSE` 的 [CWnd::EnableDynamicLayout](../Topic/CWnd::EnableDynamicLayout.md)。  
  
    ```  
    pDialog->EnableDynamicLayout(FALSE);  
    ```  
  
##### 从资源文件以编程方式设置动态布局  
  
1.  使用 [CMFCDynamicLayout::MoveHorizontalAndVertical](../Topic/CMFCDynamicLayout::MoveHorizontalAndVertical.md) 方法，以在指定动态布局信息的相关资源脚本文件（.rc 文件）中指定资源名称，如下面的示例所示：  
  
    ```  
    dynamicLayout->LoadResource("IDD_DIALOG1");  
    ```  
  
     已命名的资源必须引用包含资源文件中以 AFX\_DIALOG\_LAYOUT 条目形式存在的布局信息的对话框，如下面的示例所示：  
  
    ```  
    /////////////////////////////////////////////////////////////////////////////  
    //  
    // AFX_DIALOG_LAYOUT  
    //  
  
    IDD_MFCAPPLICATION1_DIALOG AFX_DIALOG_LAYOUT  
    BEGIN  
        0x0000, 0x6400, 0x0028, 0x643c, 0x0028  
    END  
  
    IDD_DIALOG1 AFX_DIALOG_LAYOUT  
    BEGIN  
        0x0000, 0x6464, 0x0000, 0x6464, 0x0000, 0x0000, 0x6464, 0x0000, 0x0000  
  
    END  
    ```  
  
## 请参阅  
 [CMFCDynamicLayout 类](../mfc/reference/cmfcdynamiclayout-class.md)   
 [控件类](../mfc/control-classes.md)   
 [对话框类](../mfc/dialog-box-classes.md)   
 [Dialog Editor](../mfc/dialog-editor.md)