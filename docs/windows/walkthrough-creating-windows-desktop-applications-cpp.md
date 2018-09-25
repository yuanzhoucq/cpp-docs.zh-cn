---
title: 演练： 创建传统的 Windows 桌面应用程序 （c + +） |Microsoft Docs
ms.custom: get-started-article
ms.date: 09/18/2018
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Windows applications [C++], Win32
- Windows Desktop applications [C++]
- Windows API [C++]
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7e9541517852696073a3dbbff560bb6c44fd3264
ms.sourcegitcommit: 92c568e9466ffd7346a4120c478c9bdea61c8756
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2018
ms.locfileid: "47029666"
---
# <a name="walkthrough-create-a-traditional-windows-desktop-application-c"></a>演练： 创建传统的 Windows 桌面应用程序 （c + +）

本演练演示如何在 Visual Studio 中创建的传统 Windows 桌面应用程序。 示例应用程序将创建使用 Windows API 来显示"Hello，Windows 桌面 ！" 应用程序。 可以将本演练中开发的代码作为模式来创建其他 Windows 桌面应用程序。

Windows API （也称为 Win32 API、 Windows 桌面 API 和 Windows 经典 API） 是一个基于 C 语言框架，用于创建 Windows 应用程序。 它已在上世纪 80 年代以来存在并已用于几十年来创建 Windows 应用程序。 此 API，如 MFC、 ATL 和.NET framework 之上构建了更高级和简单程序的框架。 即使最新式代码 UWP 和应用商店应用编写的 C + + WinRT 使用此 API 下方。 有关 Windows API 的详细信息，请参阅[Windows API 索引](/windows/desktop/apiindex/windows-api-list)。 有许多方法来创建 Windows 应用程序，但这是第一个。

> [!IMPORTANT]
> 为了简洁起见，在文本中省略了某些代码语句。 [生成代码](#build-the-code)本文档末尾部分显示的完整代码。

## <a name="prerequisites"></a>系统必备

- 运行 Microsoft Windows 7 或更高版本的计算机。 我们建议获取最佳开发体验的 Windows 10。

- Visual Studio 2017 的副本。 有关如何下载和安装 Visual Studio 的信息，请参阅[安装 Visual Studio](/visualstudio/install/install-visual-studio)。 当您运行安装程序时，请确保**使用 c + + 的桌面开发**检查工作负荷。 别担心，如果您未安装 Visual Studio 时安装此工作负荷。 可以再次运行安装程序并立即安装。

   ![使用 c + + 的桌面开发](../build/media/desktop-development-with-cpp.png "使用 c + + 的桌面开发")

- 使用 Visual Studio IDE 的基础知识的了解。 如果使用过 Windows 桌面应用程序之前，您可能可以跟上。 有关的介绍，请参阅[Visual Studio IDE 功能导览](/visualstudio/ide/visual-studio-ide)。

- 足够多要跟着介绍一起操作的 c + + 语言的基础知识的了解。 别担心，我们不执行任何操作太复杂。

## <a name="create-a-windows-desktop-project"></a>创建 Windows 桌面项目

请按照这些步骤创建第一个 Windows 桌面项目，并输入一个有效的 Windows 桌面应用程序的代码。 如果使用早于 Visual Studio 2017 版本 15.3 的 Visual Studio 的版本，跳到[在 Visual Studio 2017 RTM 中创建 Windows 桌面项目](#create-in-vs2017-rtm)。

### <a name="to-create-a-windows-desktop-project-in-visual-studio-2017-update-153-and-later"></a>若要创建 Windows 桌面项目在 Visual Studio 2017 Update 15.3 及更高版本

1. 在“文件”菜单上选择“新建”，再选择“项目”。

1. 在中**新的项目**对话框中，在左窗格中，展开**已安装** > **Visual c + +**，然后选择**Windows 桌面**. 在中间窗格中，选择**Windows 桌面向导**。

   在中**名称**框中，例如，键入项目的名称*DesktopApp*。 选择 **“确定”**。

   ![DesktopApp 项目命名为](../build/media/desktop-app-new-project-name-153.png "DesktopApp 项目命名为")

1. 在中**Windows 桌面项目**对话框下**应用程序类型**，选择**Windows 应用程序 (.exe)**。 在“附加选项” 下，选择“空项目” 。 选择**确定**创建项目。

   ![在 Windows 桌面项目向导中创建 DesktopApp](../build/media/desktop-app-new-project-wizard-153.png "Windows 桌面项目向导中创建 DesktopApp")

1. 在中**解决方案资源管理器**，右键单击**DesktopApp**项目中，选择**添加**，然后选择**新项**。

   ![到 DesktopApp 项目添加新项](../build/media/desktop-app-project-add-new-item-153.gif "到 DesktopApp 项目添加新项")

1. 在“添加新项”  对话框中选择“C++ 文件(.cpp)” 。 在中**名称**框中，例如，键入文件的名称*HelloWindowsDesktop.cpp*。 选择“添加”。

   ![将.cpp 文件添加到项目 DesktopApp](../build/media/desktop-app-add-cpp-file-153.png "将.cpp 文件添加到 DesktopApp 项目")

现已创建你的项目，在编辑器中打开源文件。 若要继续，跳到[创建的代码](#create-the-code)。

### <a id="create-in-vs2017-rtm"></a> 若要在 Visual Studio 2017 RTM 中创建 Windows 桌面项目

1. 在“文件”菜单上选择“新建”，再选择“项目”。

1. 在中**新的项目**对话框中，在左窗格中，展开**已安装** > **模板** > **Visual c + +**，然后选择**Win32**。 在中间窗格中，选择“Win32 项目” 。

   在中**名称**框中，例如，键入项目的名称*DesktopApp*。 选择 **“确定”**。

   ![DesktopApp 项目命名为](../build/media/desktop-app-new-project-name-150.png "DesktopApp 项目命名为")

1. 上**概述**页**Win32 应用程序向导**，选择**下一步**。

   ![在概述 Win32 应用程序向导创建 DesktopApp](../build/media/desktop-app-win32-wizard-overview-150.png "DesktopApp 创建在 Win32 应用程序向导概述")

1. 上**应用程序设置**页面上，在**应用程序类型**，选择**Windows 应用程序**。 在“附加选项” 下，选择“空项目” 。 选择**完成**创建项目。

   ![在 Win32 应用程序向导设置中创建 DesktopApp](../build/media/desktop-app-win32-wizard-settings-150.png "在 Win32 应用程序向导设置中创建 DesktopApp")

1. 在中**解决方案资源管理器**，右键单击 DesktopApp 项目，选择**添加**，然后选择**新项**。

   ![到 DesktopApp 项目添加新项](../build/media/desktop-app-project-add-new-item-150.gif "到 DesktopApp 项目添加新项")

1. 在“添加新项”  对话框中选择“C++ 文件(.cpp)” 。 在中**名称**框中，例如，键入文件的名称*HelloWindowsDesktop.cpp*。 选择“添加”。

   ![将.cpp 文件添加到项目 DesktopApp](../build/media/desktop-app-add-cpp-file-150.png "将.cpp 文件添加到 DesktopApp 项目")

现已创建你的项目，在编辑器中打开源文件。

## <a name="create-the-code"></a>创建代码

接下来，您将了解如何在 Visual Studio 中创建 Windows 桌面应用程序的代码。

### <a name="to-start-a-windows-desktop-application"></a>启动 Windows 桌面应用程序

1. 只需为每个 C 应用程序和 c + + 应用程序必须具有`main`函数作为起始点，每个 Windows 桌面应用程序必须具有`WinMain`函数。 `WinMain` 具有以下语法。

   ```cpp
   int CALLBACK WinMain(
      _In_ HINSTANCE hInstance,
      _In_ HINSTANCE hPrevInstance,
      _In_ LPSTR     lpCmdLine,
      _In_ int       nCmdShow
   );
   ```

   有关参数和此函数的返回值的信息，请参阅[WinMain 入口点](https://msdn.microsoft.com/library/windows/desktop/ms633559)。

   > [!NOTE]
   > 什么是所有这些多余的字词，如`CALLBACK`，或`HINSTANCE`，或`_In_`？ 传统的 Windows API 使用 typedef 和预处理器宏来全面抽象出的类型和特定于平台的详细信息的一些代码，调用约定，如 **__declspec**声明，以及编译器杂注。 在 Visual Studio 中，您可以使用 IntelliSense[快速信息](/visualstudio/ide/using-intellisense#quick-info)功能来查看这些 typedef 和宏的定义。 经过单词感兴趣，请将鼠标悬停或选中它，然后按**Ctrl**+**K**， **Ctrl**+**我**为包含定义的小弹出窗口。 有关详细信息，请参阅[使用 IntelliSense](/visualstudio/ide/using-intellisense)。 参数和返回类型通常使用*SAL 注释*来帮助你捕获编程错误。 有关详细信息，请参阅[使用 SAL 注释减少 C/c + + 代码缺陷](/visualstudio/code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects)。

1. Windows 桌面程序需要&lt;windows.h >。 &lt;tchar.h > 定义`TCHAR`宏，最终解析到**wchar_t**如果在项目中定义了 UNICODE 符号，否则它将解析为**char**。  如果始终生成与支持 UNICODE，不需要 TCHAR 和可以只需使用**wchar_t**直接。

   ```cpp
   #include <windows.h>
   #include <tchar.h>
   ```

1. 除了 `WinMain` 函数，每个 Windows 桌面应用程序还必须具有一个窗口过程函数。 此函数通常名为`WndProc`但你可以将其命名任意命名。 `WndProc` 具有以下语法。

   ```cpp
   LRESULT CALLBACK WndProc(
      _In_ HWND   hwnd,
      _In_ UINT   uMsg,
      _In_ WPARAM wParam,
      _In_ LPARAM lParam
   );
   ```

   此函数中编写代码来处理*消息*从 Windows 应用程序接收时*事件*发生。 例如，如果用户在应用程序中选择确定按钮，Windows 将向您发送一条消息，可以编写代码在`WndProc`会执行任何工作所适用的函数。 这称为*处理*事件。 仅处理你的应用程序的相关的事件。

   有关详细信息，请参阅[窗口过程](https://msdn.microsoft.com/library/windows/desktop/ms632593)。

### <a name="to-add-functionality-to-the-winmain-function"></a>向 WinMain 函数添加功能

1. 在中`WinMain`函数，填充类型的结构[WNDCLASSEX](https://msdn.microsoft.com/library/windows/desktop/ms633577)。 此结构包含有关窗口，例如，应用程序图标、 窗口中，要显示在标题栏中，并且非常重要的是，到你的窗口过程函数指针的名称的背景色的信息。 下面的示例演示一个典型 `WNDCLASSEX` 结构。

   ```cpp
   WNDCLASSEX wcex;

   wcex.cbSize         = sizeof(WNDCLASSEX);
   wcex.style          = CS_HREDRAW | CS_VREDRAW;
   wcex.lpfnWndProc    = WndProc;
   wcex.cbClsExtra     = 0;
   wcex.cbWndExtra     = 0;
   wcex.hInstance      = hInstance;
   wcex.hIcon          = LoadIcon(hInstance, IDI_APPLICATION);
   wcex.hCursor        = LoadCursor(NULL, IDC_ARROW);
   wcex.hbrBackground  = (HBRUSH)(COLOR_WINDOW+1);
   wcex.lpszMenuName   = NULL;
   wcex.lpszClassName  = szWindowClass;
   wcex.hIconSm        = LoadIcon(wcex.hInstance, IDI_APPLICATION);
   ```

   此结构字段的信息，请参阅[WNDCLASSEX](https://msdn.microsoft.com/library/windows/desktop/ms633577)。

1. 必须注册`WNDCLASSEX`与 Windows 这样它就会知道有关您的窗口以及如何将消息发送到它。 使用[RegisterClassEx](https://msdn.microsoft.com/library/windows/desktop/ms633587)函数，并将窗口类结构作为参数传递。 `_T`使用宏，因为我们使用`TCHAR`类型。

   ```cpp
   if (!RegisterClassEx(&wcex))
   {
      MessageBox(NULL,
         _T("Call to RegisterClassEx failed!"),
         _T("Windows Desktop Guided Tour"),
         NULL);

      return 1;
   }
   ```

1. 现在可以创建窗口了。 使用[CreateWindow](/windows/desktop/api/winuser/nf-winuser-createwindowa)函数。

   ```cpp
   static TCHAR szWindowClass[] = _T("DesktopApp");
   static TCHAR szTitle[] = _T("Windows Desktop Guided Tour Application");

   // The parameters to CreateWindow explained:
   // szWindowClass: the name of the application
   // szTitle: the text that appears in the title bar
   // WS_OVERLAPPEDWINDOW: the type of window to create
   // CW_USEDEFAULT, CW_USEDEFAULT: initial position (x, y)
   // 500, 100: initial size (width, length)
   // NULL: the parent of this window
   // NULL: this application does not have a menu bar
   // hInstance: the first parameter from WinMain
   // NULL: not used in this application
   HWND hWnd = CreateWindow(
      szWindowClass,
      szTitle,
      WS_OVERLAPPEDWINDOW,
      CW_USEDEFAULT, CW_USEDEFAULT,
      500, 100,
      NULL,
      NULL,
      hInstance,
      NULL
   );
   if (!hWnd)
   {
      MessageBox(NULL,
         _T("Call to CreateWindow failed!"),
         _T("Windows Desktop Guided Tour"),
         NULL);

      return 1;
   }
   ```

   此函数将返回`HWND`，它是窗口的句柄。 句柄是某种程度上类似于 Windows 使用以跟踪打开的窗口的指针。 有关详细信息，请参阅[Windows 数据类型](/windows/desktop/WinProg/windows-data-types)。

1. 此时已创建窗口，但我们仍需要告诉 Windows，使其可见。 这是此代码的作用：

   ```cpp
   // The parameters to ShowWindow explained:
   // hWnd: the value returned from CreateWindow
   // nCmdShow: the fourth parameter from WinMain
   ShowWindow(hWnd,
      nCmdShow);
   UpdateWindow(hWnd);
   ```

   所显示的窗口没有太多内容，因为尚未实现`WndProc`函数。 换而言之，应用程序尚不处理 Windows 现在将发送到它的消息。

1. 若要处理的消息，我们首先添加一个消息循环来侦听 Windows 发送的消息。 当应用程序收到一条消息时，此循环将该消息调度到你`WndProc`函数以进行处理。 该消息循环类似于以下代码。

   ```cpp
   MSG msg;
   while (GetMessage(&msg, NULL, 0, 0))
   {
      TranslateMessage(&msg);
      DispatchMessage(&msg);
   }

   return (int) msg.wParam;
   ```

   结构和消息循环中的函数的详细信息，请参阅[MSG](https://msdn.microsoft.com/library/windows/desktop/ms644958)， [GetMessage](https://msdn.microsoft.com/library/windows/desktop/ms644936)， [TranslateMessage](/windows/desktop/api/winuser/nf-winuser-translatemessage)，和[DispatchMessage](/windows/desktop/api/winuser/nf-winuser-dispatchmessage).

   此时， `WinMain` 函数类似于以下代码。

   ```cpp
   int WINAPI WinMain(HINSTANCE hInstance,
                      HINSTANCE hPrevInstance,
                      LPSTR lpCmdLine,
                      int nCmdShow)
   {
      WNDCLASSEX wcex;

      wcex.cbSize = sizeof(WNDCLASSEX);
      wcex.style          = CS_HREDRAW | CS_VREDRAW;
      wcex.lpfnWndProc    = WndProc;
      wcex.cbClsExtra     = 0;
      wcex.cbWndExtra     = 0;
      wcex.hInstance      = hInstance;
      wcex.hIcon          = LoadIcon(hInstance, IDI_APPLICATION);
      wcex.hCursor        = LoadCursor(NULL, IDC_ARROW);
      wcex.hbrBackground  = (HBRUSH)(COLOR_WINDOW+1);
      wcex.lpszMenuName   = NULL;
      wcex.lpszClassName  = szWindowClass;
      wcex.hIconSm        = LoadIcon(wcex.hInstance, IDI_APPLICATION);

      if (!RegisterClassEx(&wcex))
      {
         MessageBox(NULL,
            _T("Call to RegisterClassEx failed!"),
            _T("Windows Desktop Guided Tour"),
            NULL);

         return 1;
      }

      // Store instance handle in our global variable
      hInst = hInstance;

      // The parameters to CreateWindow explained:
      // szWindowClass: the name of the application
      // szTitle: the text that appears in the title bar
      // WS_OVERLAPPEDWINDOW: the type of window to create
      // CW_USEDEFAULT, CW_USEDEFAULT: initial position (x, y)
      // 500, 100: initial size (width, length)
      // NULL: the parent of this window
      // NULL: this application dows not have a menu bar
      // hInstance: the first parameter from WinMain
      // NULL: not used in this application
      HWND hWnd = CreateWindow(
         szWindowClass,
         szTitle,
         WS_OVERLAPPEDWINDOW,
         CW_USEDEFAULT, CW_USEDEFAULT,
         500, 100,
         NULL,
         NULL,
         hInstance,
         NULL
      );

      if (!hWnd)
      {
         MessageBox(NULL,
            _T("Call to CreateWindow failed!"),
            _T("Windows Desktop Guided Tour"),
            NULL);

         return 1;
      }

      // The parameters to ShowWindow explained:
      // hWnd: the value returned from CreateWindow
      // nCmdShow: the fourth parameter from WinMain
      ShowWindow(hWnd,
         nCmdShow);
      UpdateWindow(hWnd);

      // Main message loop:
      MSG msg;
      while (GetMessage(&msg, NULL, 0, 0))
      {
         TranslateMessage(&msg);
         DispatchMessage(&msg);
      }

      return (int) msg.wParam;
   }
   ```

### <a name="to-add-functionality-to-the-wndproc-function"></a>向 WndProc 函数添加功能

1. 若要启用 `WndProc` 函数以处理应用程序收到的消息，请实现 switch 语句。

   有一条重要的消息来处理[WM_PAINT](/windows/desktop/gdi/wm-paint)消息。 应用程序收到此消息，此时必须更新其显示窗口的一部分。 当用户将窗口移动您窗口的前面，然后将它重新移动消失时，会发生此事件。 你的应用程序不知道此类事件的发生时间;仅 Windows 知道，因此它会告诉您使用`WM_PAINT`。 当第一次显示窗口时，必须更新所有它。

   若要处理`WM_PAINT`消息，首先应调用[BeginPaint](/windows/desktop/api/winuser/nf-winuser-beginpaint)，然后处理所有的逻辑进行布局文本、 按钮和在窗口中，其他控件，然后调用[EndPaint](/windows/desktop/api/winuser/nf-winuser-endpaint)。 为此应用程序，开始调用和结束调用之间的逻辑是显示字符串"Hello，Windows 桌面 ！" “Hello，World!”。 在下面的代码，请注意[TextOut](/windows/desktop/api/wingdi/nf-wingdi-textouta)函数用于显示的字符串。

   ```cpp
   PAINTSTRUCT ps;
   HDC hdc;
   TCHAR greeting[] = _T("Hello, Windows desktop!");

   switch (message)
   {
   case WM_PAINT:
      hdc = BeginPaint(hWnd, &ps);

      // Here your application is laid out.
      // For this introduction, we just print out "Hello, Windows desktop!"
      // in the top left corner.
      TextOut(hdc,
         5, 5,
         greeting, _tcslen(greeting));
      // End application-specific layout section.

      EndPaint(hWnd, &ps);
      break;
   }
   ```

   `HDC` 在此代码是设备上下文，即 Windows 用来启用你的应用程序与图形子系统进行通信的数据结构的句柄。 `BeginPaint`和`EndPaint`函数确保你的应用程序的行为类似于一个好市民一样，但不超出其所需到更长时间使用的设备上下文。 这有助于确保图形子系统是可供其他应用程序。

1. 应用程序通常会处理许多其他消息，例如[WM_CREATE](/windows/desktop/winmsg/wm-create)首先创建一个窗口，并[WM_DESTROY](/windows/desktop/winmsg/wm-destroy)窗口关闭时。 以下代码显示基本但完整的 `WndProc` 函数。

   ```cpp
   LRESULT CALLBACK WndProc(HWND hWnd, UINT message, WPARAM wParam, LPARAM lParam)
   {
      PAINTSTRUCT ps;
      HDC hdc;
      TCHAR greeting[] = _T("Hello, Windows desktop!");

      switch (message)
      {
      case WM_PAINT:
         hdc = BeginPaint(hWnd, &ps);

         // Here your application is laid out.
         // For this introduction, we just print out "Hello, Windows desktop!"
         // in the top left corner.
         TextOut(hdc,
            5, 5,
            greeting, _tcslen(greeting));
         // End application specific layout section.

         EndPaint(hWnd, &ps);
         break;
      case WM_DESTROY:
         PostQuitMessage(0);
         break;
      default:
         return DefWindowProc(hWnd, message, wParam, lParam);
         break;
      }

      return 0;
   }
   ```

## <a name="build-the-code"></a>生成代码

正如所承诺，下面是工作应用程序的完整代码。

### <a name="to-build-this-example"></a>生成此示例

1. 删除输入中的任何代码*HelloWindowsDesktop.cpp*在编辑器中。 复制此代码示例并将其粘贴到*HelloWindowsDesktop.cpp*:

   ```cpp
   // HelloWindowsDesktop.cpp
   // compile with: /D_UNICODE /DUNICODE /DWIN32 /D_WINDOWS /c

   #include <windows.h>
   #include <stdlib.h>
   #include <string.h>
   #include <tchar.h>

   // Global variables

   // The main window class name.
   static TCHAR szWindowClass[] = _T("DesktopApp");

   // The string that appears in the application's title bar.
   static TCHAR szTitle[] = _T("Windows Desktop Guided Tour Application");

   HINSTANCE hInst;

   // Forward declarations of functions included in this code module:
   LRESULT CALLBACK WndProc(HWND, UINT, WPARAM, LPARAM);

   int CALLBACK WinMain(
      _In_ HINSTANCE hInstance,
      _In_ HINSTANCE hPrevInstance,
      _In_ LPSTR     lpCmdLine,
      _In_ int       nCmdShow
   )
   {
      WNDCLASSEX wcex;

      wcex.cbSize = sizeof(WNDCLASSEX);
      wcex.style          = CS_HREDRAW | CS_VREDRAW;
      wcex.lpfnWndProc    = WndProc;
      wcex.cbClsExtra     = 0;
      wcex.cbWndExtra     = 0;
      wcex.hInstance      = hInstance;
      wcex.hIcon          = LoadIcon(hInstance, IDI_APPLICATION);
      wcex.hCursor        = LoadCursor(NULL, IDC_ARROW);
      wcex.hbrBackground  = (HBRUSH)(COLOR_WINDOW+1);
      wcex.lpszMenuName   = NULL;
      wcex.lpszClassName  = szWindowClass;
      wcex.hIconSm        = LoadIcon(wcex.hInstance, IDI_APPLICATION);

      if (!RegisterClassEx(&wcex))
      {
         MessageBox(NULL,
            _T("Call to RegisterClassEx failed!"),
            _T("Windows Desktop Guided Tour"),
            NULL);

         return 1;
      }

      // Store instance handle in our global variable
      hInst = hInstance;

      // The parameters to CreateWindow explained:
      // szWindowClass: the name of the application
      // szTitle: the text that appears in the title bar
      // WS_OVERLAPPEDWINDOW: the type of window to create
      // CW_USEDEFAULT, CW_USEDEFAULT: initial position (x, y)
      // 500, 100: initial size (width, length)
      // NULL: the parent of this window
      // NULL: this application does not have a menu bar
      // hInstance: the first parameter from WinMain
      // NULL: not used in this application
      HWND hWnd = CreateWindow(
         szWindowClass,
         szTitle,
         WS_OVERLAPPEDWINDOW,
         CW_USEDEFAULT, CW_USEDEFAULT,
         500, 100,
         NULL,
         NULL,
         hInstance,
         NULL
      );

      if (!hWnd)
      {
         MessageBox(NULL,
            _T("Call to CreateWindow failed!"),
            _T("Windows Desktop Guided Tour"),
            NULL);

         return 1;
      }

      // The parameters to ShowWindow explained:
      // hWnd: the value returned from CreateWindow
      // nCmdShow: the fourth parameter from WinMain
      ShowWindow(hWnd,
         nCmdShow);
      UpdateWindow(hWnd);

      // Main message loop:
      MSG msg;
      while (GetMessage(&msg, NULL, 0, 0))
      {
         TranslateMessage(&msg);
         DispatchMessage(&msg);
      }

      return (int) msg.wParam;
   }

   //  FUNCTION: WndProc(HWND, UINT, WPARAM, LPARAM)
   //
   //  PURPOSE:  Processes messages for the main window.
   //
   //  WM_PAINT    - Paint the main window
   //  WM_DESTROY  - post a quit message and return
   LRESULT CALLBACK WndProc(HWND hWnd, UINT message, WPARAM wParam, LPARAM lParam)
   {
      PAINTSTRUCT ps;
      HDC hdc;
      TCHAR greeting[] = _T("Hello, Windows desktop!");

      switch (message)
      {
      case WM_PAINT:
         hdc = BeginPaint(hWnd, &ps);

         // Here your application is laid out.
         // For this introduction, we just print out "Hello, Windows desktop!"
         // in the top left corner.
         TextOut(hdc,
            5, 5,
            greeting, _tcslen(greeting));
         // End application-specific layout section.

         EndPaint(hWnd, &ps);
         break;
      case WM_DESTROY:
         PostQuitMessage(0);
         break;
      default:
         return DefWindowProc(hWnd, message, wParam, lParam);
         break;
      }

      return 0;
   }
   ```

1. 在 **“生成”** 菜单上，选择 **“生成解决方案”**。 编译的结果应出现在 Visual Studio 的**输出**窗口中。

   ![生成 DesktopApp 项目](../build/media/desktop-app-project-build-150.gif "生成 DesktopApp 项目")

1. 若要运行该应用程序，按**F5**。 一个窗口，其中包含文本"Hello，Windows 桌面 ！" 文字的窗口。

   ![运行 DesktopApp 项目](../build/media/desktop-app-project-run-157.png "运行 DesktopApp 项目")

祝贺你！ 已完成了本演练，并生成了传统的 Windows 桌面应用程序。

## <a name="see-also"></a>请参阅

[Windows 桌面应用程序](../windows/windows-desktop-applications-cpp.md)
