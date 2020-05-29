---
title: 如何：创建用户控件并承载 MDI 视图
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], Windows Forms Controls
- Windows Forms [C++], MFC support
ms.assetid: 625b5821-f923-4701-aca0-c1a4ceca4f63
ms.openlocfilehash: 72501ba32d3b8b9a5c5fd8dd0c56f0628642b147
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374458"
---
# <a name="how-to-create-the-user-control-and-host-mdi-view"></a>如何：创建用户控件并承载 MDI 视图

以下步骤演示如何创建 .NET Framework 用户控件，在控件类库中创作用户控件（特别是 Windows 控件库项目），然后将项目编译为程序集。 然后，可以从使用从[CView 类](../mfc/reference/cview-class.md)和[CWinFormsView 类](../mfc/reference/cwinformsview-class.md)派生的类的 MFC 应用程序使用该控件。

有关如何创建 Windows 窗体用户控件和创作控件类库的信息，请参阅[如何：作者用户控件](/dotnet/framework/winforms/controls/how-to-author-composite-controls)。

> [!NOTE]
> 在某些情况下，Windows 窗体控件（如第三方网格控件）在 MFC 应用程序中托管时可能无法可靠地运行。 建议的解决方法是在 MFC 应用程序中放置 Windows 窗体用户控件，并将第三方网格控件放在用户控件中。

此过程假定您创建了名为 WindowsFormsControlLibrary1 的 Windows 窗体控件库项目，根据["如何：在对话框中创建用户控件和主机](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md)"中的过程。

### <a name="to-create-the-mfc-host-application"></a>创建 MFC 主机应用程序

1. 创建 MFC 应用程序项目。

   在 **"文件**"菜单上，选择 **"新建**"，然后单击"**项目**"。 在**可视C++** 文件夹中，选择**MFC 应用程序**。

   在 **"名称"** 框中，`MFC02`输入并更改"**解决方案**"设置**以添加到解决方案**。 单击“确定”。 

   在**MFC 应用程序向导**中，接受所有默认值，然后单击 **"完成**"。 这将创建具有多个文档接口的 MFC 应用程序。

1. 为通用语言运行时 （CLR） 支持配置项目。

   在**解决方案资源管理器**中，右键单击`MFC01`项目节点，并从上下文菜单中选择 **"属性**"。 将显示"**属性页**"对话框。

   在 **"配置属性**"下，选择 **"常规**"。 在 **"项目默认值"** 部分下，将 **"通用语言运行时支持**"设置为**通用语言运行时支持 （/clr）。**

   在 **"配置属性**"下，展开**C/C++** 并单击**常规**节点。 将**调试信息格式**设置为**程序数据库 （/Zi）。**

   单击**代码生成**节点。 将**启用最小重建**设置为**否 （/Gm-）**。 还将**基本运行时检查**设置为 **"默认**"。

   单击"**确定"** 以应用更改。

1. 在*pch.h（Visual* Studio 2017 和更早版本中的*stdafx.h）* 中，添加以下行：

    ```
    #using <System.Windows.Forms.dll>
    ```

1. 添加对 .NET 控件的引用。

   在**解决方案资源管理器**中，右键单击`MFC02`项目节点并选择"**添加**"**引用**。 在 **"属性页**"中，单击"**添加新参考**"，选择 WindowsFormsControlLibrary1（在 **"项目**"选项卡下），然后单击"**确定**"。 这将以[/FU](../build/reference/fu-name-forced-hash-using-file.md)编译器选项的形式添加引用，以便程序将编译;它还将 WindowsFormsControlLibrary1.dll 复制到`MFC02`项目目录中，以便程序将运行。

1. 在 stdafx.h 中，找到此行：

    ```
    #endif // _AFX_NO_AFXCMN_SUPPORT
    ```

   在上面添加以下行：

    ```
    #include <afxwinforms.h>   // MFC Windows Forms support
    ```

1. 修改视图类，以便从[CWinFormsView](../mfc/reference/cwinformsview-class.md)继承。

   在 MFC02View.h 中，将[CView](../mfc/reference/cview-class.md)替换为[CWinFormsView，](../mfc/reference/cwinformsview-class.md)以便代码如下所示：

    ```
    class CMFC02View : public CWinFormsView
    {
    };
    ```

   如果要向 MDI 应用程序添加其他视图，则需要为创建的每个视图调用[CWinApp：：AddDocTemplate。](../mfc/reference/cwinapp-class.md#adddoctemplate)

1. 修改 MFC02View.cpp 文件，在IMPLEMENT_DYNCREATE宏和消息映射中将 CView 更改为 CWinFormsView，并将现有的空构造函数替换为如下所示的构造函数：

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

   在**解决方案资源管理器**中，右键单击 MFC02 并选择 **"设置为启动项目**"。

   在“生成”**** 菜单中，单击“生成解决方案”****。

   在 **"调试"** 菜单上，单击"**不调试即可开始**"。

## <a name="see-also"></a>另请参阅

[以 MFC 视图的形式承载 Windows 窗体用户控件](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)
