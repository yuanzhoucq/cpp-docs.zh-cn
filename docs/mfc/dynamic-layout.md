---
title: 动态布局 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 7518e2fdd07254b8b1991fae8a41f26058920858
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33350844"
---
# <a name="dynamic-layout"></a>动态布局
使用 Visual Studio 2015 中的 MFC，你可以创建用户可以调整大小的对话框，你可以控制调整布局以更改大小的方式。 例如，可以将对话框底部的按钮附加到下边缘，使其始终保持在底部。 还可以将某些控件（如列表框、编辑框和文本字段）设置为在用户展开对话框时展开。  
  
## <a name="specifying-dynamic-layout-settings-for-an-mfc-dialog-box"></a>为 MFC 对话框指定动态布局设置  
 当用户调整对话框大小时，该对话框中的控件可以调整大小，或沿 X 和 Y 方向移动。 用户重新调整对话框大小时控件大小或位置的更改称为动态布局。 例如，以下是调整大小之前的对话框：  
  
 ![调整大小前的对话框。] (../mfc/media/mfcdynamiclayout4.png "mfcdynamiclayout4")  
  
 调整大小后，列表框区域会增大，以显示更多项，并且以下按钮将沿右下角移动：  
  
 ![调整大小后的对话框。] (../mfc/media/mfcdynamiclayout5.png "mfcdynamiclayout5")  
  
 可以通过在 IDE 的资源编辑器中对每个控件指定详细信息来控制动态布局，也可以通过访问特定控件的 CMFCDynamicLayout 对象并设置其属性以编程方式执行操作。  
  
### <a name="setting-dynamic-layout-properties-in-the-resource-editor"></a>在资源编辑器中设置动态布局属性  
 可以使用资源编辑器设置对话框的动态布局行为，而无需编写任何代码。  
  
##### <a name="to-set-dynamic-layout-properties-in-the-resource-editor"></a>在资源编辑器中设置动态布局属性  
  
1.  打开一个 MFC 项目，打开想要在对话框编辑器中使用的对话框。  
  
     ![在资源编辑器中打开对话框。] (../mfc/media/mfcdynamiclayout3.png "mfcdynamiclayout3")  
  
2.  选择一个控件，然后在属性窗口中，设置其动态布局属性。 **动态布局**属性窗口中的一部分包含属性**移动类型**，**调整大小类型**，并且，具体取决于选择这些属性的值定义多少控件的特定属性将移动或更改大小。 **移动类型**确定如何移动控件更改对话框的大小;**调整大小类型**确定控件的大小调整为对话框的大小已更改。 **移动类型**和**调整大小类型**可能**水平**，**垂直**，**同时**，或**无**具体取决于你想要动态更改的维度。 水平是 X 维度；垂直是 Y 方向。  
  
3.  如果您希望控件如按钮在固定的大小并保持不变右下方，一样是很常见的**确定**或**取消**按钮、 设置**调整大小类型**到**无**，并设置**移动类型**到**同时**。 有关**移动 X**和**移动 Y**值下**移动类型**，设置为 100%，若要使要保持固定的距离底部右下角的控件。  
  
     ![动态布局](../mfc/media/mfcdynamiclayout1.png "mfcdynamiclayout1")  
  
4.  假设你还有一个希望在对话框展开时展开的控件。 通常情况下，用户可能会展开对话框，以展开多行编辑框，从而增加文本区域的大小，他们也可能会展开列表控件，以查看更多的数据。 这种情况下，设置**调整大小类型**两者都，并设置**移动类型**为 none。 然后，设置**调整大小 X**和**调整大小 Y**为 100 的值。  
  
     ![动态布局设置](../mfc/media/mfcdynamiclayout2.png "mfcdynamiclayout2")  
  
5.  使用可能对你的控件有意义的其他值进行试验。 具有单行文本框的对话框可能具有**调整大小类型**设置为**水平**仅，例如。  
  
### <a name="setting-dynamic-layout-properties-programmatically"></a>以编程方式设置动态布局属性  
 之前的过程适用于在设计时为对话框指定动态布局属性，但如果希望在运行时控制动态布局，则可以采用编程方式设置动态布局属性。  
  
##### <a name="to-set-dynamic-layout-properties-programmatically"></a>以编程方式设置动态布局属性  
  
1.  在自己对话框类的实现代码中查找或创建一个想要为该对话指定动态布局的位置。 例如，你可能希望在对话框中添加一个方法（如 `AdjustLayout`），并从不要更改布局的位置进行调用。 你可能会首先从构造函数中调用，也可能在对对话框进行更改之后调用。  
  
2.  对话框，请调用[GetDynamicLayout](../mfc/reference/cwnd-class.md#getdynamiclayout)，CWnd 类的方法。 GetDynamicLayout 返回了指向 CMFCDynamicLayout 对象的指针。  
  
 ```  
    CMFCDynamicLayout* dynamicLayout = pDialog->GetDynamicLayout();

 ```  
  
3.  对于你想要添加动态行为的第一个控件，使用的静态方法的动态布局类上创建[MoveSettings](../mfc/reference/cmfcdynamiclayout-class.md#movesettings_structure)应调整控件的方式进行编码的结构。 执行此操作通过首先选择适当的静态方法： [cmfcdynamiclayout:: Movehorizontal](../mfc/reference/cmfcdynamiclayout-class.md#movehorizontal)， [cmfcdynamiclayout:: Movevertical](../mfc/reference/cmfcdynamiclayout-class.md#movevertical)， [cmfcdynamiclayout:: Movenone](../mfc/reference/cmfcdynamiclayout-class.md#movenone)，或[cmfcdynamiclayout:: Movehorizontalandvertical](../mfc/reference/cmfcdynamiclayout-class.md#movehorizontalandvertical)。 对移动的水平和/或垂直特性传入一个百分比。 这些静态方法都将返回新创建的 MoveSettings 对象，你可以使用该对象来指定控件的移动行为。  
  
     记住，100 表示完全根据该对话框更改的大小进行移动，这会导致控件的边缘与新边框保持固定的距离。  
  
 ```  
    MoveSettings moveSettings = CMFCDynamicLayout::MoveHorizontal(100);

 ```  
  
4.  执行相同的操作使用的大小行为[SizeSettings](../mfc/reference/cmfcdynamiclayout-class.md#sizesettings_structure)类型。 例如，若要指定当对话框调整大小时控件不会更改大小，请使用以下代码：  
  
 ```  
    SizeSettings sizeSettings = CMFCDynamicLayout::SizeNone();

 ```  
  
5.  将控件添加到动态布局管理器使用[cmfcdynamiclayout:: Additem](../mfc/reference/cmfcdynamiclayout-class.md#additem)方法。 指定所需控件的不同方法有两种重载。 一种重载使用控件的窗口句柄 (HWND)，另一种使用控件 ID。  
  
 ```  
    dynamicLayout->AddItem(hWndControl,
    moveSettings,
    sizeSettings);

 ```  
  
6.  对每个需要移动或调整大小的控件进行重复。  
  
7.  如果有必要，可以使用[cmfcdynamiclayout:: Hasitem](../mfc/reference/cmfcdynamiclayout-class.md#hasitem)方法来确定控件是否已在经过动态布局更改的控件的列表或[cmfcdynamiclayout:: Isempty](../mfc/reference/cmfcdynamiclayout-class.md#isempty)若要确定是否存在任何可能发生更改的控件的方法。  
  
8.  若要启用对话框布局，请调用[cwnd:: Enabledynamiclayout](../mfc/reference/cwnd-class.md#enabledynamiclayout)方法。  
  
 ```  
    pDialog->EnableDynamicLayout(TRUE);

 ```  
  
9. 下次用户调整大小的对话框中， [cmfcdynamiclayout:: Adjust](../mfc/reference/cmfcdynamiclayout-class.md#adjust)方法调用实际应用设置。  
  
10. 如果你想要禁用动态布局，调用[cwnd:: Enabledynamiclayout](../mfc/reference/cwnd-class.md#enabledynamiclayout)与`FALSE`同样适用于`bEnabled`参数。  
  
 ```  
    pDialog->EnableDynamicLayout(FALSE);

 ```  
  
##### <a name="to-set-the-dynamic-layout-programmatically-from-a-resource-file"></a>从资源文件以编程方式设置动态布局  
  
1.  使用[cmfcdynamiclayout:: Movehorizontalandvertical](../mfc/reference/cmfcdynamiclayout-class.md#movehorizontalandvertical)方法，以指定动态布局信息，如以下示例所示的相关资源脚本文件 （.rc 文件） 中指定的资源名称：  
  
 ```  
    dynamicLayout->LoadResource("IDD_DIALOG1");

 ```  
  
     已命名的资源必须引用包含资源文件中以 AFX_DIALOG_LAYOUT 条目形式存在的布局信息的对话框，如下面的示例所示：  
  
 ' * / / * / / * / / AFX_DIALOG_LAYOUT * / /  
 
    IDD_MFCAPPLICATION1_DIALOG AFX_DIALOG_LAYOUT  
    开始 0X0000、 0X6400、 0X0028、 0X643C、 0X0028  
    End 
 
    IDD_DIALOG1 AFX_DIALOG_LAYOUT  
    开始 0X0000、 0X6464、 0X0000、 0X6464、 0X0000、 0X0000、 0X6464、 0X0000、 0X0000  
 
    End 
 ```  
  
## See Also  
 [CMFCDynamicLayout Class](../mfc/reference/cmfcdynamiclayout-class.md)   
 [Control Classes](../mfc/control-classes.md)   
 [Dialog Box Classes](../mfc/dialog-box-classes.md)   
 [Dialog Editor](../windows/dialog-editor.md)

