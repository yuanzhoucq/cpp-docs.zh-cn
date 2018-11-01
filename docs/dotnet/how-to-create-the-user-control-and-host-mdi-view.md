---
title: 如何：创建用户控件并承载 MDI 视图
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], Windows Forms Controls
- Windows Forms [C++], MFC support
ms.assetid: 625b5821-f923-4701-aca0-c1a4ceca4f63
ms.openlocfilehash: c2705ef1938684d8521316436fccaae367629584
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50509117"
---
# <a name="how-to-create-the-user-control-and-host-mdi-view"></a>如何：创建用户控件并承载 MDI 视图

以下步骤说明如何创建.NET Framework 用户控件、 创作控件类库 （具体而言，Windows 控件库项目） 中的用户控件，然后将项目编译为程序集。 从 MFC 应用程序使用派生自的类也可以使用该控件[CView 类](../mfc/reference/cview-class.md)并[CWinFormsView 类](../mfc/reference/cwinformsview-class.md)。

有关如何创建 Windows 窗体用户控件和创作控件类库的信息，请参阅[如何： 创作用户控件](/dotnet/framework/winforms/controls/how-to-author-composite-controls)。

> [!NOTE]
>  在某些情况下，Windows 窗体控件，如第三方网格控件，行为可能不可靠的 MFC 应用程序中托管时。 建议的解决方法是将 Windows 窗体用户控件放置在 MFC 应用程序中，进行深入了解用户控制的第三方网格控件。

此过程假定你创建 Windows 窗体控件库项目中的过程根据名为 WindowsFormsControlLibrary1[如何： 在对话框中创建用户控件并承载](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md)。

### <a name="to-create-the-mfc-host-application"></a>若要创建 MFC 宿主应用程序

1. 创建 MFC 应用程序项目。

   上**文件**菜单中，选择**新建**，然后单击**项目**。 在中**Visual c + +** 文件夹，选择**MFC 应用程序**。

   在中**名称**框中，输入`MFC02`并将更改**解决方案**设置为**将添加到解决方案**。 单击 **“确定”**。

   在中**MFC 应用程序向导**，接受所有默认值，然后单击**完成**。 这将创建具有多文档界面的 MFC 应用程序。

1. 配置公共语言运行时 (CLR) 支持的项目。

   在中**解决方案资源管理器**，右键单击`MFC01`项目节点，然后选择**属性**从上下文菜单。 **属性页**对话框随即出现。

   下**配置属性**，选择**常规**。 下**项目默认值**部分中，设置**公共语言运行时支持**到**公共语言运行时支持 (/ clr)**。

   下**配置属性**，展开**C/c + +** 然后单击**常规**节点。 设置**调试信息格式**到**程序数据库 (/Zi)**。

   单击**代码生成**节点。 设置**启用最小重新生成**到**否 (/ Gm-)**。 此外设置**基本运行时检查**到**默认**。

   单击**确定**应用所做的更改。

1. 在 stdafx.h 中，添加以下行：

    ```
    #using <System.Windows.Forms.dll>
    ```

1. 添加对.NET 控件的引用。

   在中**解决方案资源管理器**，右键单击`MFC02`项目节点，然后选择**添加**，**引用**。 在中**属性页**，单击**添加新引用**，选择 WindowsFormsControlLibrary1 (下**项目**选项卡)，然后单击**确定**. 这在的窗体添加的引用[/FU](../build/reference/fu-name-forced-hash-using-file.md)编译器选项，以便程序进行编译; 它还将 windowsformscontrollibrary1.dll 复制到`MFC02`项目目录，以便运行该程序。

1. 在 stdafx.h 中，找到以下行：

    ```
    #endif // _AFX_NO_AFXCMN_SUPPORT
    ```

   添加上面的这些行：

    ```
    #include <afxwinforms.h>   // MFC Windows Forms support
    ```

1. 修改视图类，以便它继承自[CWinFormsView](../mfc/reference/cwinformsview-class.md)。

   在 MFC02View.h 中，替换[CView](../mfc/reference/cview-class.md)与[CWinFormsView](../mfc/reference/cwinformsview-class.md) ，以便该代码会出现，如下所示：

    ```
    class CMFC02View : public CWinFormsView
    {
    };
    ```

   如果你想将附加视图添加到 MDI 应用程序，你将需要调用[CWinApp::AddDocTemplate](../mfc/reference/cwinapp-class.md#adddoctemplate)为你创建的每个视图。

1. 修改 MFC02View.cpp 文件以将 CView 更改为 CWinFormsView，IMPLEMENT_DYNCREATE 宏和消息映射中，现有空构造函数替换为构造函数如下所示：

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

   在中**解决方案资源管理器**，右键单击 MFC02 并选择**设为启动项目**。

   在 **“生成”** 菜单上，单击 **“生成解决方案”**。

   上**调试**菜单上，单击**启动但不调试**。

## <a name="see-also"></a>请参阅

[以 MFC 视图的形式承载 Windows 窗体用户控件](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)