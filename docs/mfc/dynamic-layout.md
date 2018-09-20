---
title: 动态布局 |Microsoft Docs
ms.custom: ''
ms.date: 06/25/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 8598cfb2-c8d4-4f5a-bf2b-59dc4653e042
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 08fc6f6a5b93851468d412e34b3ee0a85ab534e5
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46413245"
---
# <a name="dynamic-layout"></a>动态布局

使用 Visual Studio 2015 中的 MFC，可以创建对话的用户可以调整大小，并可以控制布局调整大小的更改的方式。 例如，可以将对话框底部的按钮附加到下边缘，使其始终保持在底部。 还可以将某些控件（如列表框、编辑框和文本字段）设置为在用户展开对话框时展开。

## <a name="specifying-dynamic-layout-settings-for-an-mfc-dialog-box"></a>为 MFC 对话框指定动态布局设置

当用户调整对话框大小时，该对话框中的控件可以调整大小，或沿 X 和 Y 方向移动。 用户重新调整对话框大小时控件大小或位置的更改称为动态布局。 例如，以下是调整大小之前的对话框：

![调整大小前的对话框。](../mfc/media/mfcdynamiclayout4.png "mfcdynamiclayout4")

调整大小后，列表框区域会增大，以显示更多项，并且以下按钮将沿右下角移动：

![调整大小后的对话框。](../mfc/media/mfcdynamiclayout5.png "mfcdynamiclayout5")

可以通过指定的资源编辑器在 IDE 中的每个控件的详细信息来控制动态布局，也可以通过访问因此以编程方式执行操作`CMFCDynamicLayout`特定控件对象并设置其属性。

### <a name="setting-dynamic-layout-properties-in-the-resource-editor"></a>在资源编辑器中设置动态布局属性

可以使用资源编辑器设置对话框的动态布局行为，而无需编写任何代码。

#### <a name="to-set-dynamic-layout-properties-in-the-resource-editor"></a>在资源编辑器中设置动态布局属性

1. 打开一个 MFC 项目，打开想要在对话框编辑器中使用的对话框。

     ![在资源编辑器中打开该对话框。](../mfc/media/mfcdynamiclayout3.png "mfcdynamiclayout3")

2. 选择一个控件，然后在属性窗口中，设置其动态布局属性。 **动态布局**属性窗口中的部分包含的属性**移动类型**，**调整大小类型**，和，具体取决于选择为这些属性的值定义多少控件的特定属性将移动或更改大小。 **将类型移动**确定在移动控件如何为对话框的大小已更改;**调整大小类型**确定控件的大小调整为对话框的大小已更改。 **将类型移动**并**调整大小类型**可能**水平**，**垂直**，**同时**，或**无**具体取决于你想要动态更改的维度。 水平是 X 维度；垂直是 Y 方向。

3. 如果你想在固定的大小并将保持不变右下角的按钮等控件，按原样常见**确定**或**取消**按钮，设置**调整大小类型**到**无**，并设置**移动类型**到**同时**。 有关**移动 X**并**移动 Y**值下**移动类型**，设置为 100%可使控件保持固定的距离底部右下角。

     ![动态布局](../mfc/media/mfcdynamiclayout1.png "mfcdynamiclayout1")

4. 假设你还有一个希望在对话框展开时展开的控件。 通常情况下，用户可能会展开对话框，以展开多行编辑框，从而增加文本区域的大小，他们也可能会展开列表控件，以查看更多的数据。 这种情况下，设置**调整大小类型**到两者，并设置**移动类型**为 none。 然后，设置**调整大小 X**并**调整大小 Y**为 100 的值。

     ![动态布局设置](../mfc/media/mfcdynamiclayout2.png "mfcdynamiclayout2")

5. 使用可能对你的控件有意义的其他值进行试验。 包含单行文本框的对话框可能**调整大小类型**设置为**水平**仅用于示例。

### <a name="setting-dynamic-layout-properties-programmatically"></a>以编程方式设置动态布局属性

之前的过程适用于在设计时为对话框指定动态布局属性，但如果希望在运行时控制动态布局，则可以采用编程方式设置动态布局属性。

#### <a name="to-set-dynamic-layout-properties-programmatically"></a>以编程方式设置动态布局属性

1. 在自己对话框类的实现代码中查找或创建一个想要为该对话指定动态布局的位置。 例如，你可能希望在对话框中添加一个方法（如 `AdjustLayout`），并从不要更改布局的位置进行调用。 你可能会首先从构造函数中调用，也可能在对对话框进行更改之后调用。

2. 对于对话框中，调用[GetDynamicLayout](../mfc/reference/cwnd-class.md#getdynamiclayout)，方法的`CWnd`类。 `GetDynamicLayout` 返回一个指向`CMFCDynamicLayout`对象。

    ```cpp
    CMFCDynamicLayout* dynamicLayout = pDialog->GetDynamicLayout();
    ```

3. 对于你想要添加动态行为的第一个控件，使用静态方法的动态布局类上创建[MoveSettings](../mfc/reference/cmfcdynamiclayout-class.md#movesettings_structure)控件的调整的方式进行编码的结构。 执行此操作通过首先选择适当的静态方法： [cmfcdynamiclayout:: Movehorizontal](../mfc/reference/cmfcdynamiclayout-class.md#movehorizontal)， [cmfcdynamiclayout:: Movevertical](../mfc/reference/cmfcdynamiclayout-class.md#movevertical)， [cmfcdynamiclayout:: Movenone](../mfc/reference/cmfcdynamiclayout-class.md#movenone)，或[cmfcdynamiclayout:: Movehorizontalandvertical](../mfc/reference/cmfcdynamiclayout-class.md#movehorizontalandvertical)。 对移动的水平和/或垂直特性传入一个百分比。 这些静态方法都将返回新创建的 MoveSettings 对象，你可以使用该对象来指定控件的移动行为。

   记住，100 表示完全根据该对话框更改的大小进行移动，这会导致控件的边缘与新边框保持固定的距离。

    ```cpp
    MoveSettings moveSettings = CMFCDynamicLayout::MoveHorizontal(100);
    ```

4. 执行相同的操作使用的大小行为[SizeSettings](../mfc/reference/cmfcdynamiclayout-class.md#sizesettings_structure)类型。 例如，若要指定当对话框调整大小时控件不会更改大小，请使用以下代码：

    ```cpp
    SizeSettings sizeSettings = CMFCDynamicLayout::SizeNone();
    ```

5. 将控件添加到使用动态布局管理器[cmfcdynamiclayout:: Additem](../mfc/reference/cmfcdynamiclayout-class.md#additem)方法。 指定所需控件的不同方法有两种重载。 一种重载使用控件的窗口句柄 (HWND)，另一种使用控件 ID。

    ```cpp
    dynamicLayout->AddItem(hWndControl,
    moveSettings,
    sizeSettings);
    ```

6. 对每个需要移动或调整大小的控件进行重复。

7. 如果有必要，可以使用[cmfcdynamiclayout:: Hasitem](../mfc/reference/cmfcdynamiclayout-class.md#hasitem)方法，以确定控件是否已在经过动态布局更改控件的列表或[cmfcdynamiclayout:: Isempty](../mfc/reference/cmfcdynamiclayout-class.md#isempty)若要确定是否有可能会有所更改任何控件的方法。

8. 若要启用对话框布局，请调用[cwnd:: Enabledynamiclayout](../mfc/reference/cwnd-class.md#enabledynamiclayout)方法。

    ```cpp
    pDialog->EnableDynamicLayout(TRUE);
    ```

9. 在用户调整对话框中，在下次[cmfcdynamiclayout:: Adjust](../mfc/reference/cmfcdynamiclayout-class.md#adjust)方法调用实际应用设置。

10. 如果你想要禁用动态布局，则调用[cwnd:: Enabledynamiclayout](../mfc/reference/cwnd-class.md#enabledynamiclayout)与**FALSE**同样适用于*bEnabled*参数。

    ```cpp
    pDialog->EnableDynamicLayout(FALSE);
    ```

#### <a name="to-set-the-dynamic-layout-programmatically-from-a-resource-file"></a>从资源文件以编程方式设置动态布局

1. 使用[cmfcdynamiclayout:: Movehorizontalandvertical](../mfc/reference/cmfcdynamiclayout-class.md#movehorizontalandvertical)方法，以指定动态布局信息，如以下示例所示的相关资源脚本文件 （.rc 文件） 中指定资源名称：

    ```cpp
    dynamicLayout->LoadResource("IDD_DIALOG1");
    ```

     已命名的资源必须引用包含中的窗体的布局信息的对话框**AFX_DIALOG_LAYOUT**中的资源文件，如以下示例所示的条目：

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

## <a name="see-also"></a>请参阅

[CMFCDynamicLayout 类](../mfc/reference/cmfcdynamiclayout-class.md)<br/>
[控件类](../mfc/control-classes.md)<br/>
[对话框类](../mfc/dialog-box-classes.md)<br/>
[对话框编辑器](../windows/dialog-editor.md)<br/>
[在 Visual c + + 2015年中的 mfc 动态对话框布局](https://mariusbancila.ro/blog/2015/07/27/dynamic-dialog-layout-for-mfc-in-visual-c-2015/)
