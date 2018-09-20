---
title: 演练： 向应用程序添加 CTaskDialog |Microsoft Docs
ms.custom: ''
ms.date: 06/28/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CTaskDialog, adding
- walkthroughs [MFC], dialogs
ms.assetid: 3a62abb8-2d86-4bec-bdb8-5784d5f9a9f8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0f803af896c1bb2a0e5f58e45f4ef9f588f4e66d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46420474"
---
# <a name="walkthrough-adding-a-ctaskdialog-to-an-application"></a>演练：向应用程序添加 CTaskDialog

本演练介绍了 [CTaskDialog Class](../mfc/reference/ctaskdialog-class.md) ，并演示如何将其添加到应用程序中。

`CTaskDialog`是替换 Windows 消息框在 Windows Vista 或更高版本的任务对话框。 `CTaskDialog` 改进了原始消息框并添加了功能。 在 Visual Studio 中仍支持 Windows 消息框。

> [!NOTE]
> 以前的 Windows 版本高于 Windows Vista 不支持`CTaskDialog`。 如果你想要向在早期版本的 Windows 上运行你的应用程序的用户显示一条消息，则必须编写备用对话框选项的程序。 可以使用静态方法 [CTaskDialog::IsSupported](../mfc/reference/ctaskdialog-class.md#issupported) 在运行时确定用户的计算机能否显示 `CTaskDialog`中的 Windows 消息框。 此外，仅当应用程序使用 Unicode 库生成时， `CTaskDialog` 才可用。

`CTaskDialog` 支持使用多种可选元素来收集和显示信息。 例如， `CTaskDialog` 可以显示命令链接、自定义按钮、自定义图标和页脚。 `CTaskDialog` 还具有多种方法，可查询任务对话框状态以确定用户选择的可选元素。

## <a name="prerequisites"></a>系统必备

你需要以下组件来完成本演练：

- Visual Studio 2010 或更高版本

- Windows Vista 或更高版本

## <a name="replacing-a-windows-message-box-with-a-ctaskdialog"></a>将 Windows 消息框替换为 CTaskDialog

以下过程演示了将要替换 Windows 消息框的 `CTaskDialog`最基本的用法。 此示例还更改了与任务对话框关联的图标。 更改该图标会使 `CTaskDialog` 的外观与 Windows 消息框相同。

### <a name="to-replace-a-windows-message-box-with-a-ctaskdialog"></a>将 Windows 消息框替换为 CTaskDialog 的步骤

1. 使用默认设置创建一个新的 MFC 应用程序项目。 调用它*MyProject*。

2. 使用 **解决方案资源管理器** 打开文件 MyProject.cpp。

3. 在包含列表后面添加 `#include "afxtaskdialog.h"` 。

4. 查找 `CMyProjectApp::InitInstance`方法。 在 `return TRUE;` 语句的前面插入以下代码行。 此代码将创建我们在 Windows 消息框或 `CTaskDialog`中使用的字符串。

    ```cpp
    CString message("My message to the user");
    CString dialogTitle("My Task Dialog title");
    CString emptyString;
    ```

5. 在步骤 4 中的代码的后面添加以下代码。 此代码可保证用户的计算机支持 `CTaskDialog`。 如果不支持该对话框，应用程序将改为显示 Windows 消息框。

    ```cpp
    if (CTaskDialog::IsSupported())
    {

    }
    else
    {
        AfxMessageBox(message);
    }
    ```

6. 在步骤 5 中 `if` 语句后面的括号之间插入以下代码。 此代码将创建 `CTaskDialog`。

    ```cpp
    CTaskDialog taskDialog(message, emptyString, dialogTitle, TDCBF_OK_BUTTON);
    ```

7. 在下一行上，添加以下代码。 此代码将设置警告图标。

    ```cpp
    taskDialog.SetMainIcon(TD_WARNING_ICON);
    ```

8. 在下一行上，添加以下代码。 此代码将显示任务对话框。

    ```cpp
    taskDialog.DoModal();
    ```

如果不希望 `CTaskDialog` 显示与 Windows 消息框相同的图标，可以忽略步骤 7。 如果忽略该步骤，当应用程序显示 `CTaskDialog` 时，该对话框没有图标。

编译并运行该应用程序。 在启动后，应用程序将显示任务对话框。

## <a name="adding-functionality-to-the-ctaskdialog"></a>向 CTaskDialog 添加功能

以下过程演示如何向在前述过程中创建的 `CTaskDialog` 添加功能。 示例代码演示如何基于用户选择执行特定指令。

### <a name="to-add-functionality-to-the-ctaskdialog"></a>向 CTaskDialog 添加功能的步骤

1. 导航到**资源视图**。 如果无法看到**资源视图**，可以将其打开**视图**菜单。

2. 展开**资源视图**直到可以选择**字符串表**文件夹。 展开它，然后双击**字符串表**条目。

3. 滚动到字符串表的底部并添加一个新条目。 将 ID 更改为 `TEMP_LINE1`。 将标题设置为 **Command Line 1**。

4. 再添加一个新条目。 将 ID 更改为 `TEMP_LINE2`。 将标题设置为 **Command Line 2**。

5. 导航回到 MyProject.cpp。

6. 在 `CString emptyString;`的后面添加以下代码：

    ```cpp
    CString expandedLabel("Hide extra information");
    CString collapsedLabel("Show extra information");
    CString expansionInfo("This is the additional information to the user,\nextended over two lines.");
    ```

7. 找到 `taskDialog.DoModal()` 语句并替换为以下代码。 此代码将更新任务对话框并添加新控件：

    ```cpp
    taskDialog.SetMainInstruction(L"Warning");
    taskDialog.SetCommonButtons(
        TDCBF_YES_BUTTON | TDCBF_NO_BUTTON | TDCBF_CANCEL_BUTTON);
    taskDialog.LoadCommandControls(TEMP_LINE1, TEMP_LINE2);
    taskDialog.SetExpansionArea(
        expansionInfo, collapsedLabel, expandedLabel);
    taskDialog.SetFooterText(L"This is the a small footnote to the user");
    taskDialog.SetVerificationCheckboxText(L"Remember your selection");
    ```

8. 添加以下代码行，该代码将向用户显示任务对话框并检索用户的选择：

    ```cpp
    INT_PTR result = taskDialog.DoModal();
    ```

9. 在调用 `taskDialog.DoModal()`之后，插入以下代码。 此段代码将处理用户的输入：

    ```cpp
    if (taskDialog.GetVerificationCheckboxState())
    {
        // PROCESS IF the user selects the verification checkbox
    }

    switch (result)
    {
    case TEMP_LINE1:
        // PROCESS IF the first command line
        break;
    case TEMP_LINE2:
        // PROCESS IF the second command line
        break;
    case IDYES:
        // PROCESS IF the user clicks yes
        break;
    case IDNO:
        // PROCESS IF the user clicks no
        break;
    case IDCANCEL:
        // PROCESS IF the user clicks cancel
        break;
    default:
        // This case should not be hit because closing
        // the dialog box results in IDCANCEL
        break;
    }
    ```

在步骤 9 的代码中，将以 PROCESS IF 开头的注释替换为要在指定条件下执行的代码。

编译并运行该应用程序。 应用程序将显示使用新控件和其他信息的任务对话框。

## <a name="displaying-a-ctaskdialog-without-creating-a-ctaskdialog-object"></a>显示 CTaskDialog 而不创建 CTaskDialog 对象

以下过程演示如何在不先创建 `CTaskDialog` 对象的情况下显示 `CTaskDialog` 。 本示例继续前面的过程。

### <a name="to-display-a-ctaskdialog-without-creating-a-ctaskdialog-object"></a>显示 CTaskDialog 而不创建 CTaskDialog 对象的步骤

1. 打开 MyProject.cpp 文件（如果尚未打开）。

2. 导航到 `if (CTaskDialog::IsSupported())` 语句的右括号处。

3. 直接在 `if` 语句的右括号前面（ `else` 块的前面）插入以下代码：

    ```cpp
    HRESULT result2 = CTaskDialog::ShowDialog(L"My error message",
        L"Error",
        L"New Title",
        TEMP_LINE1,
        TEMP_LINE2);
    ```

编译并运行该应用程序。 应用程序将显示两个任务对话框。 第一个对话框来自“向 CTaskDialog 添加功能的步骤”过程；第二个对话框来自上一个过程。

这些示例并未演示 `CTaskDialog`的所有可用选项，但是可以帮助你入门。 有关该类的完整描述，请参阅 [CTaskDialog Class](../mfc/reference/ctaskdialog-class.md) 。

## <a name="see-also"></a>请参阅

[对话框](../mfc/dialog-boxes.md)<br/>
[CTaskDialog 类](../mfc/reference/ctaskdialog-class.md)<br/>
[CTaskDialog::CTaskDialog](../mfc/reference/ctaskdialog-class.md#ctaskdialog)
