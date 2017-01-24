---
title: "如何：创建用户控件并承载 MDI 视图 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MFC [C++], Windows 窗体控件"
  - "Windows 窗体 [C++], MFC 支持"
ms.assetid: 625b5821-f923-4701-aca0-c1a4ceca4f63
caps.latest.revision: 25
caps.handback.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：创建用户控件并承载 MDI 视图
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下列步骤说明如何创建 .NET Framework 用户控件、创作控件类库（特别是 Windows 控件库项目）中的用户控件，然后将项目编译为程序集。  然后，可以从 MFC 应用程序中使用控件，该应用程序使用派生自 [CView Class](../mfc/reference/cview-class.md) 和 [CWinFormsView Class](../mfc/reference/cwinformsview-class.md) 的类。  
  
 有关如何创建 Windows 窗体用户控件和创作控件类库的信息，请参见[如何：创作用户控件](../Topic/How%20to:%20Author%20Composite%20Controls.md)。  
  
> [!NOTE]
>  在某些情况下，Windows 窗体控件（例如第三方网格控件）当在 MFC 应用程序中被承载时行为可能不可靠。  建议的解决方法是：将 Windows 窗体用户控件放置在 MFC 应用程序中，而将第三方网格控件放置在用户控件中。  
  
 此过程假定您按照[如何：创建用户控件并将它承载在对话框中](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md)中的过程创建了名为 WindowsFormsControlLibrary1 的 Windows 窗体控件库项目。  
  
### 创建 MFC 宿主应用程序  
  
1.  创建 MFC 应用程序项目。  
  
     在**“文件”**菜单上，选择**“新建”**，然后单击**“项目”**。  在**“Visual C\+\+”**文件夹中，选择**“MFC 应用程序”**。  
  
     在“名称”框中，输入 `MFC02`，并将“解决方案”设置更改为“添入解决方案”。  单击**“确定”**。  
  
     在**“MFC 应用程序向导”**中，接受所有默认值，然后单击**“完成”**。  这就创建了一个具有多文档界面的 MFC 应用程序。  
  
2.  配置项目以获得公共语言运行时 \(CLR\) 支持。  
  
     在“解决方案资源管理器”中，右击 `MFC01` 项目节点，然后从上下文菜单中选择“属性”。  将显示**“属性页”**对话框。  
  
     在**“配置属性”**下选择**“常规”**。  在**“项目默认值”**部分下，将**“公共语言运行时支持”**设置为**“公共语言运行时支持\(\/clr\)”**。  
  
     在**“配置属性”**下，展开**“C\/C\+\+”**，然后单击**“常规”**节点。  将**“调试信息格式”**设置为**“程序数据库\(\/Zi\)”**。  
  
     单击**“代码生成”**节点。  将**“启用最小重新生成”**设置为**“否\(\/Gm\-\)”**。  另外，将**“基本运行时检查”**设置为**“默认”**。  
  
     单击**“确定”**应用所做的更改。  
  
3.  在 stdafx.h 中，添加下列行：  
  
    ```  
    #using <System.Windows.Forms.dll>  
    ```  
  
4.  向 .NET 控件添加引用。  
  
     在解决方案资源管理器中，右击 `MFC02` 项目节点，然后选择“添加”、“引用”。  在“属性页”中，单击“添加新引用”，选择“WindowsFormsControlLibrary1”（在“项目”选项卡下），然后单击“确定”。  此操作添加一个 [\/FU](../build/reference/fu-name-forced-hash-using-file.md) 编译器选项形式的引用，以便程序进行编译；它还将 WindowsFormsControlLibrary1.dll 复制到 `MFC02` 项目目录中，以便程序运行。  
  
5.  在 stdafx.h 中，请找到以下行：  
  
    ```  
    #endif // _AFX_NO_AFXCMN_SUPPORT   
    ```  
  
     在此行上面添加这些行：  
  
    ```  
    #include <afxwinforms.h>   // MFC Windows Forms support  
    ```  
  
6.  修改视图类以便它从 [CWinFormsView](../mfc/reference/cwinformsview-class.md) 继承。  
  
     在 MFC02View.h 中，将 [CView](../mfc/reference/cview-class.md) 替换为 [CWinFormsView](../mfc/reference/cwinformsview-class.md)，以便出现如下所示的代码：  
  
    ```  
    class CMFC02View : public CWinFormsView  
    {  
    };  
    ```  
  
     如果希望将附加视图添加到 MDI 应用程序，需要为创建的每个视图调用 [CWinApp::AddDocTemplate](../Topic/CWinApp::AddDocTemplate.md)。  
  
7.  修改 MFC02View.cpp 文件以将 IMPLEMENT\_DYNCREATE 宏和消息映射中的 CView 更改为 CWinFormsView，并且将现有空构造函数替换为下面显示的构造函数：  
  
    ```  
    IMPLEMENT_DYNCREATE(CMFC02View, CWinFormsView)  
  
    CMFC02View::CMFC02View(): CWinFormsView(WindowsFormsControlLibrary1::UserControl1::typeid)   
    {  
    }  
    BEGIN_MESSAGE_MAP(CMFC02View, CWinFormsView)  
    //leave existing body as is  
    END_MESSAGE_MAP()  
    ```  
  
8.  生成并运行该项目。  
  
     在**“解决方案资源管理器”**中，右击“MFC02”并选择**“设为启动项目”**。  
  
     在**“生成”**菜单上，单击**“生成解决方案”**。  
  
     在**“调试”**菜单上，单击**“开始执行\(不调试\)”**。  
  
## 请参阅  
 [以 MFC 视图的形式承载 Windows 窗体用户控件](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)