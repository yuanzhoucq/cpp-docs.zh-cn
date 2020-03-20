---
title: 如何：创建用户控件并承载 MDI 视图
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], Windows Forms Controls
- Windows Forms [C++], MFC support
ms.assetid: 625b5821-f923-4701-aca0-c1a4ceca4f63
ms.openlocfilehash: 634dd9c1ad2ce9199cec0dfa7ef067bd45f242f6
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/20/2019
ms.locfileid: "79544722"
---
# <a name="how-to-create-the-user-control-and-host-mdi-view"></a>如何：创建用户控件并承载 MDI 视图

下面的步骤演示如何创建 .NET Framework 用户控件、在控件类库中创作用户控件（具体而言，还指 Windows 控件库项目），然后将项目编译为程序集。 然后，可以从使用派生自[CView 类](../mfc/reference/cview-class.md)和[CWinFormsView 类](../mfc/reference/cwinformsview-class.md)的类的 MFC 应用程序中使用控件。

有关如何创建 Windows 窗体用户控件和创作控件类库的信息，请参阅[如何：创作用户控件](/dotnet/framework/winforms/controls/how-to-author-composite-controls)。

> [!NOTE]
>  在某些情况下，当托管在 MFC 应用程序中时，Windows 窗体控件（例如第三方网格控件）可能不会正常运行。 建议的解决方法是将 Windows 窗体用户控件放置在 MFC 应用程序中，并将第三方网格控件放在用户控件中。

此过程假定你已创建了一个名为 WindowsFormsControlLibrary1 的 Windows 窗体控件库项目，如[如何：创建用户控件和在对话框中承载](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md)"中所述。

### <a name="to-create-the-mfc-host-application"></a>创建 MFC 宿主应用程序

1. 创建 MFC 应用程序项目。

   在 "**文件**" 菜单上，选择 "**新建**"，然后单击 "**项目**"。 在**视觉对象C++** 文件夹中，选择 " **MFC 应用程序**"。

   在 "**名称**" 框中，输入 `MFC02` 并将 "**解决方案**" 设置更改为 "**添加到解决方案**"。 单击“确定”。

   在**MFC 应用程序向导**中，接受所有默认值，然后单击 "**完成**"。 这会创建包含多个文档界面的 MFC 应用程序。

1. 为公共语言运行时（CLR）支持配置项目。

   在**解决方案资源管理器**中，右键单击 "`MFC01` 项目" 节点，然后从上下文菜单中选择 "**属性**"。 "**属性页**" 对话框随即出现。

   在 "**配置属性**" 下选择 "**常规**"。 在 "**项目默认值**" 部分下，将 "**公共语言运行时支持**" 设置为**公共语言运行时支持（/clr）** 。

   在 "**配置属性**" 下，展开 " **C/C++**  " 并单击 "**常规**" 节点。 将 "**调试信息格式**" 设置为 "**程序数据库（/zi）** "。

   单击 "**代码生成**" 节点。 将 "**启用最小重新生成**" 设置为 "**否" （/Gm-）** 。 还将**基本运行时检查**设置为**默认值**。

   单击 **"确定"** 以应用所做的更改。

1. 在*pch* （Visual Studio 2017 及更早版本中的*stdafx.h* ）中添加以下行：

    ```
    #using <System.Windows.Forms.dll>
    ```

1. 添加对 .NET 控件的引用。

   在**解决方案资源管理器**中，右键单击 `MFC02` 项目节点，然后选择 "**添加**"、"**引用**"。 在**属性页**中，单击 **"添加新引用**"，选择 "WindowsFormsControlLibrary1" （在 "**项目**" 选项卡下），然后单击 **"确定"** 。 这会添加一个[/FU](../build/reference/fu-name-forced-hash-using-file.md)编译器选项形式的引用，以便程序进行编译;它还会将 WindowsFormsControlLibrary1 复制到 `MFC02` 项目目录中，以便程序运行。

1. 在 stdafx.h 中，查找以下行：

    ```
    #endif // _AFX_NO_AFXCMN_SUPPORT
    ```

   将这些行添加到它上面：

    ```
    #include <afxwinforms.h>   // MFC Windows Forms support
    ```

1. 修改视图类，使其继承自[CWinFormsView](../mfc/reference/cwinformsview-class.md)。

   在 MFC02View 中，将[CView](../mfc/reference/cview-class.md)替换为[CWinFormsView](../mfc/reference/cwinformsview-class.md) ，使代码如下所示：

    ```
    class CMFC02View : public CWinFormsView
    {
    };
    ```

   如果要将其他视图添加到 MDI 应用程序，则需要为创建的每个视图调用[CWinApp：： AddDocTemplate](../mfc/reference/cwinapp-class.md#adddoctemplate) 。

1. 修改 MFC02View 文件，以将 CWinFormsView 中的 CView 更改为 IMPLEMENT_DYNCREATE 宏和消息映射中的，并将现有的空构造函数替换为下面所示的构造函数：

    ```
    IMPLEMENT_DYNCREATE(CMFC02View, CWinFormsView)

    CMFC02View::CMFC02View(): CWinFormsView(WindowsFormsControlLibrary1::UserControl1::typeid)
    {
    }
    BEGIN_MESSAGE_MAP(CMFC02View, CWinFormsView)
    //leave existing body as is
    END_MESSAGE_MAP()
    ```

1. 生成并运行该项目。

   在**解决方案资源管理器**中，右键单击 "MFC02" 并选择 "**设为启动项目**"。

   在“生成”菜单中，单击“生成解决方案”。

   在 "**调试**" 菜单上，单击 "**启动（不调试**）"。

## <a name="see-also"></a>另请参阅

[以 MFC 视图的形式承载 Windows 窗体用户控件](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)
