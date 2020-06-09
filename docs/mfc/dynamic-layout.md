---
title: 动态布局
ms.date: 09/09/2019
ms.assetid: 8598cfb2-c8d4-4f5a-bf2b-59dc4653e042
ms.openlocfilehash: 3108e7bae0be216dfb877d03c87fdc17ef7d69f2
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624751"
---
# <a name="dynamic-layout"></a>动态布局

在 Visual Studio 2015 中，可以创建用户可调整其大小的对话框，还可以控制布局调整大小更改的方式。 例如，可以将对话框底部的按钮附加到下边缘，使其始终保持在底部。 还可以将某些控件（如列表框、编辑框和文本字段）设置为在用户展开对话框时展开。

## <a name="specifying-dynamic-layout-settings-for-an-mfc-dialog-box"></a>为 MFC 对话框指定动态布局设置

当用户调整对话框大小时，该对话框中的控件可以调整大小，或沿 X 和 Y 方向移动。 用户重新调整对话框大小时控件大小或位置的更改称为动态布局。 例如，以下是调整大小之前的对话框：

![调整大小前的对话框。](../mfc/media/mfcdynamiclayout4.png "调整大小前的对话框。")

调整大小后，列表框区域会增大，以显示更多项，并且以下按钮将沿右下角移动：

![调整大小后的对话框。](../mfc/media/mfcdynamiclayout5.png "调整大小后的对话框。")

可以通过在 IDE 的资源编辑器中指定每个控件的详细信息来控制动态布局，也可以通过访问 `CMFCDynamicLayout` 特定控件的对象并设置属性以编程方式来控制动态布局。

### <a name="setting-dynamic-layout-properties-in-the-resource-editor"></a>在资源编辑器中设置动态布局属性

可以使用资源编辑器设置对话框的动态布局行为，而无需编写任何代码。

#### <a name="to-set-dynamic-layout-properties-in-the-resource-editor"></a>在资源编辑器中设置动态布局属性

1. 打开一个 MFC 项目，打开想要在对话框编辑器中使用的对话框。

   ![在资源编辑器中打开对话框。](../mfc/media/mfcdynamiclayout3.png "在资源编辑器中打开对话框。")

1. 选择控件，并在 "**属性**" 窗口（在**类视图**中）设置其动态布局属性。 "**属性**" 窗口中的 "**动态布局**" 部分包含 "**移动类型**" 和 "**调整大小类型**" 属性，具体取决于为这些属性选择的值、用于定义控件移动或更改大小的特定属性。 **移动类型**确定控件在对话框大小变化时的移动方式;**大小调整类型**确定如何在对话框大小更改时调整控件的大小。 **移动类型**和**大小调整类型**可以是**水平**、**垂直**、**两者**或**无**，具体取决于要动态更改的维度。 水平是 X 维度；垂直是 Y 方向。

1. 如果希望控件（如按钮）为固定大小并在右下方停留，就像 **"确定" 或 "取消"** 按钮一样常见，将 " **Cancel** **大小调整类型**" 设置为 "**无**"，并将 "**移动类型**" 设置为 "**两者**"。 对于 "**移动类型**" 下的 "**移动 X** " 和 "**移动 Y** " 值，请将 "100%" 设置为使控件远离右下角的固定距离。

   ![动态布局](../mfc/media/mfcdynamiclayout1.png "动态布局")

1. 假设你还有一个希望在对话框展开时展开的控件。 通常情况下，用户可能会展开对话框，以展开多行编辑框，从而增加文本区域的大小，他们也可能会展开列表控件，以查看更多的数据。 对于这种情况，请将**大小调整类型**设置为这两个，并将 "**移动类型**" 设置为 "无"。 然后，将 Y**大小调整 X**和**大小调整 Y**值设置为100。

   ![动态布局设置](../mfc/media/mfcdynamiclayout2.png "动态布局设置")

1. 使用可能对你的控件有意义的其他值进行试验。 例如，具有单行文本框的对话框可能将**调整大小类型**设置为 "**水平**"。

### <a name="setting-dynamic-layout-properties-programmatically"></a>以编程方式设置动态布局属性

之前的过程适用于在设计时为对话框指定动态布局属性，但如果希望在运行时控制动态布局，则可以采用编程方式设置动态布局属性。

#### <a name="to-set-dynamic-layout-properties-programmatically"></a>以编程方式设置动态布局属性

1. 在自己对话框类的实现代码中查找或创建一个想要为该对话指定动态布局的位置。 例如，你可能希望在对话框中添加一个方法（如 `AdjustLayout`），并从不要更改布局的位置进行调用。 你可能会首先从构造函数中调用，也可能在对对话框进行更改之后调用。

1. 对于对话框，请调用[GetDynamicLayout](reference/cwnd-class.md#getdynamiclayout)，它是类的方法 `CWnd` 。 `GetDynamicLayout` 返回一个指向 `CMFCDynamicLayout` 对象的指针。

    ```cpp
    CMFCDynamicLayout* dynamicLayout = pDialog->GetDynamicLayout();
    ```

1. 对于要向其添加动态行为的第一个控件，请使用动态布局类上的静态方法来创建[MoveSettings](reference/cmfcdynamiclayout-class.md#movesettings_structure)结构，以便对控件的调整方式进行编码。 为此，首先选择适当的静态方法： [CMFCDynamicLayout：： MoveHorizontal](reference/cmfcdynamiclayout-class.md#movehorizontal)、 [CMFCDynamicLayout：： MoveVertical](reference/cmfcdynamiclayout-class.md#movevertical)、 [CMFCDynamicLayout：： MoveNone](reference/cmfcdynamiclayout-class.md#movenone)或[CMFCDynamicLayout：： MoveHorizontalAndVertical](reference/cmfcdynamiclayout-class.md#movehorizontalandvertical)。 对移动的水平和/或垂直特性传入一个百分比。 这些静态方法都将返回新创建的 MoveSettings 对象，你可以使用该对象来指定控件的移动行为。

   记住，100 表示完全根据该对话框更改的大小进行移动，这会导致控件的边缘与新边框保持固定的距离。

    ```cpp
    MoveSettings moveSettings = CMFCDynamicLayout::MoveHorizontal(100);
    ```

1. 对大小行为（使用[SizeSettings](reference/cmfcdynamiclayout-class.md#sizesettings_structure)类型）执行相同的操作。 例如，若要指定当对话框调整大小时控件不会更改大小，请使用以下代码：

    ```cpp
    SizeSettings sizeSettings = CMFCDynamicLayout::SizeNone();
    ```

1. 使用[CMFCDynamicLayout：： AddItem](reference/cmfcdynamiclayout-class.md#additem)方法将控件添加到动态布局管理器。 指定所需控件的不同方法有两种重载。 一种重载使用控件的窗口句柄 (HWND)，另一种使用控件 ID。

    ```cpp
    dynamicLayout->AddItem(hWndControl,
    moveSettings,
    sizeSettings);
    ```

1. 对每个需要移动或调整大小的控件进行重复。

1. 如有必要，可以使用[CMFCDynamicLayout：： HasItem](reference/cmfcdynamiclayout-class.md#hasitem)方法来确定控件是否已在受动态布局更改的控件列表上，或使用[CMFCDynamicLayout：： IsEmpty](reference/cmfcdynamiclayout-class.md#isempty)方法来确定是否有任何受更改的控件。

1. 若要启用对话布局，请调用[CWnd：： EnableDynamicLayout](reference/cwnd-class.md#enabledynamiclayout)方法。

    ```cpp
    pDialog->EnableDynamicLayout(TRUE);
    ```

1. 用户下一次调整对话框的大小时，将调用[CMFCDynamicLayout：：调节](reference/cmfcdynamiclayout-class.md#adjust)方法，实际应用这些设置。

1. 如果要禁用动态布局，请调用*bEnabled*参数的[CWnd：： EnableDynamicLayout](reference/cwnd-class.md#enabledynamiclayout)和**FALSE** 。

    ```cpp
    pDialog->EnableDynamicLayout(FALSE);
    ```

#### <a name="to-set-the-dynamic-layout-programmatically-from-a-resource-file"></a>从资源文件以编程方式设置动态布局

1. 使用[CMFCDynamicLayout：： MoveHorizontalAndVertical](reference/cmfcdynamiclayout-class.md#movehorizontalandvertical)方法可以指定相关资源脚本文件（.rc 文件）中指定动态布局信息的资源名称，如以下示例中所示：

    ```cpp
    dynamicLayout->LoadResource("IDD_DIALOG1");
    ```

   命名资源必须以资源文件中**AFX_DIALOG_LAYOUT**条目的形式引用包含布局信息的对话框，如以下示例中所示：

    ```RC
    /////////////////////////////////////////////////////////////////////////////
    //
    // AFX_DIALOG_LAYOUT
    //

    IDD_MFCAPPLICATION1_DIALOG AFX_DIALOG_LAYOUT
    BEGIN
    0x0000,
    0x6400,
    0x0028,
    0x643c,
    0x0028
    END

    IDD_DIALOG1 AFX_DIALOG_LAYOUT
    BEGIN
    0x0000,
    0x6464,
    0x0000,
    0x6464,
    0x0000,
    0x0000,
    0x6464,
    0x0000,
    0x0000

    END
    ```

## <a name="see-also"></a>另请参阅

[CMFCDynamicLayout 类](reference/cmfcdynamiclayout-class.md)<br/>
[控件类](control-classes.md)<br/>
[对话框类](dialog-box-classes.md)<br/>
[对话框编辑器](../windows/dialog-editor.md)<br/>
[Visual C++ 2015 中 MFC 的动态对话框布局](https://mariusbancila.ro/blog/2015/07/27/dynamic-dialog-layout-for-mfc-in-visual-c-2015/)
