---
title: "演练：创建 Windows 桌面应用程序 (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
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
  - "Windows 应用程序 [C++], Win32"
  - "WinMain"
  - "Win32 应用程序 [C++]"
  - "Windows API [C++]"
ms.assetid: a247a9af-aff1-4899-9577-5f8104a0afbb
caps.latest.revision: 27
caps.handback.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 演练：创建 Windows 桌面应用程序 (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本演练演示如何创建在窗口中显示“Hello，World\!”的基本 Windows 桌面 应用程序。 可以将本演练中开发的代码作为模式来创建其他 Windows 桌面应用程序。  
  
 Win32 API（也称为 Windows API）是一个基于 C 的框架，用于创建 Windows 应用程序。 有关 Win32 API 的更多信息，请参阅 [Windows API](https://msdn.microsoft.com/en-us/library/cc433218.aspx)。  
  
> [!IMPORTANT]
>  以便我们可以在本文档的步骤中更加清楚地介绍特定代码段，我们可能会省略某些代码语句，除非运行的应用程序需要；例如，include 指令和全局变量声明。 本文档末尾的**示例**部分显示完整代码。  
  
## 系统必备  
 若要完成本演练，你必须了解 C\+\+ 语言的基础知识。  
  
 有关视频演示，请参阅 [视频帮助：在 Visual Studio 2008 文档中创建 Win32 应用程序 \(C\+\+\)](http://go.microsoft.com/fwlink/?LinkId=102471)。  
  
### 创建基于 Win32 的项目  
  
1.  在**文件**菜单上，单击**新建**，然后单击**项目**。  
  
2.  在“新建项目”对话框的左窗格中，依次单击“已安装模板”和“Visual C\+\+”，然后选择“Win32”。 在中间窗格中，选择“Win32 项目”。  
  
     在“名称”框中，键入项目名称，例如`win32app`。 单击“确定”。  
  
3.  在“Win32 应用程序向导”的欢迎页面中，单击“下一步”。  
  
4.  在“应用程序设置”页的“应用程序类型”下，选择“Windows 应用程序”。 在“附加选项”下，选择“空项目”。 单击“完成”以创建项目。  
  
5.  在“解决方案资源管理器”中，右键单击 Win32app 项目，然后依次单击“添加”和“新建项”。 在“添加新项”对话框中选择“C\+\+ 文件\(.cpp\)”。 在“名称”框中，键入文件名，例如`GT_HelloWorldWin32.cpp`。 单击**“添加”**。  
  
### 启动 Windows 桌面应用程序  
  
1.  正如每个 C 应用程序和 C\+\+ 应用程序在起始点必须具有 `main` 函数，每个基于 Win32 的应用程序的函数也必须具有 `WinMain` 函数。`WinMain` 具有以下语法。  
  
    ```  
    int WINAPI WinMain(HINSTANCE hInstance, HINSTANCE hPrevInstance, LPSTR lpCmdLine, int nCmdShow);  
    ```  
  
     有关此函数的参数和返回值的详细信息，请参阅 [WinMain 函数](http://msdn.microsoft.com/library/windows/desktop/ms633559)。  
  
2.  由于应用程序代码必须使用现有定义，因此应向文件中添加包含语句。  
  
    ```  
    #include <windows.h> #include <stdlib.h> #include <string.h> #include <tchar.h>  
    ```  
  
3.  除了 `WinMain` 函数，每个 Windows 桌面应用程序还必须具有一个窗口过程函数。 此函数通常名为 `WndProc`。`WndProc` 具有以下语法。  
  
    ```  
    LRESULT CALLBACK WndProc(HWND, UINT, WPARAM, LPARAM);  
    ```  
  
     此函数处理应用程序从操作系统中接收的大量*消息*。 例如，如果应用程序的对话框中有“确定”按钮，那么用户单击该按钮时，操作系统会向应用程序发送一条消息，通知按钮已被单击。`WndProc` 负责对该事件作出响应。 在本例中，相应的响应可能是关闭对话框。  
  
     有关详细信息，请参阅[窗口过程](http://msdn.microsoft.com/library/windows/desktop/ms632593)。  
  
### 向 WinMain 函数添加功能  
  
1.  在 `WinMain` 函数中，创建 [WNDCLASSEX](http://msdn.microsoft.com/library/windows/desktop/ms633577) 类型的窗口类结构。 此结构包含关于窗口的信息，例如应用程序图标、窗口背景色、标题栏中显示的名称、窗口过程函数的名称等。 下面的示例演示一个典型 `WNDCLASSEX` 结构。  
  
    ```  
    WNDCLASSEX wcex; wcex.cbSize = sizeof(WNDCLASSEX); wcex.style          = CS_HREDRAW | CS_VREDRAW; wcex.lpfnWndProc    = WndProc; wcex.cbClsExtra     = 0; wcex.cbWndExtra     = 0; wcex.hInstance      = hInstance; wcex.hIcon          = LoadIcon(hInstance, MAKEINTRESOURCE(IDI_APPLICATION)); wcex.hCursor        = LoadCursor(NULL, IDC_ARROW); wcex.hbrBackground  = (HBRUSH)(COLOR_WINDOW+1); wcex.lpszMenuName   = NULL; wcex.lpszClassName  = szWindowClass; wcex.hIconSm        = LoadIcon(wcex.hInstance, MAKEINTRESOURCE(IDI_APPLICATION));  
    ```  
  
     有关此结构字段的信息，请参阅 [WNDCLASSEX](http://msdn.microsoft.com/library/windows/desktop/ms633577)。  
  
2.  现在已创建了窗口类，必须进行注册。 使用 [RegisterClassEx](http://msdn.microsoft.com/library/windows/desktop/ms633587) 函数，并将窗口类结构作为参数传递。  
  
    ```  
    if (!RegisterClassEx(&wcex)) { MessageBox(NULL, _T("Call to RegisterClassEx failed!"), _T("Win32 Guided Tour"), NULL); return 1; }  
    ```  
  
3.  现在可以创建窗口了。 使用 [CreateWindow](http://msdn.microsoft.com/library/windows/desktop/ms632679) 函数。  
  
    ```  
    static TCHAR szWindowClass[] = _T("win32app"); static TCHAR szTitle[] = _T("Win32 Guided Tour Application"); // The parameters to CreateWindow explained: // szWindowClass: the name of the application // szTitle: the text that appears in the title bar // WS_OVERLAPPEDWINDOW: the type of window to create // CW_USEDEFAULT, CW_USEDEFAULT: initial position (x, y) // 500, 100: initial size (width, length) // NULL: the parent of this window // NULL: this application does not have a menu bar // hInstance: the first parameter from WinMain // NULL: not used in this application HWND hWnd = CreateWindow( szWindowClass, szTitle, WS_OVERLAPPEDWINDOW, CW_USEDEFAULT, CW_USEDEFAULT, 500, 100, NULL, NULL, hInstance, NULL ); if (!hWnd) { MessageBox(NULL, _T("Call to CreateWindow failed!"), _T("Win32 Guided Tour"), NULL); return 1; }  
    ```  
  
     此函数会返回 HWND，这是一个窗口的句柄。 有关详细信息，请参阅 [Windows 数据类型](http://msdn.microsoft.com/library/windows/desktop/aa383751)。  
  
4.  现在，使用以下代码来显示窗口。  
  
    ```  
    // The parameters to ShowWindow explained: // hWnd: the value returned from CreateWindow // nCmdShow: the fourth parameter from WinMain ShowWindow(hWnd, nCmdShow); UpdateWindow(hWnd);  
    ```  
  
     此时，由于没有实现 `WndProc` 函数，因而所显示的窗口内容不多。  
  
5.  现在，添加用于侦听操作系统所发送消息的消息循环。 当应用程序收到一条消息时，此循环将该消息调度到 `WndProc` 函数以进行处理。 该消息循环类似于以下代码。  
  
    ```  
    MSG msg; while (GetMessage(&msg, NULL, 0, 0)) { TranslateMessage(&msg); DispatchMessage(&msg); } return (int) msg.wParam;  
    ```  
  
     有关消息循环中的结构和函数的详细信息，请参阅 [MSG](http://msdn.microsoft.com/library/windows/desktop/ms644958)、[GetMessage](http://msdn.microsoft.com/library/windows/desktop/ms644936)、[TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) 和 [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934)。  
  
     此时，`WinMain` 函数类似于以下代码。  
  
    ```  
    int WINAPI WinMain(HINSTANCE hInstance, HINSTANCE hPrevInstance, LPSTR lpCmdLine, int nCmdShow) { WNDCLASSEX wcex; wcex.cbSize = sizeof(WNDCLASSEX); wcex.style          = CS_HREDRAW | CS_VREDRAW; wcex.lpfnWndProc    = WndProc; wcex.cbClsExtra     = 0; wcex.cbWndExtra     = 0; wcex.hInstance      = hInstance; wcex.hIcon          = LoadIcon(hInstance, MAKEINTRESOURCE(IDI_APPLICATION)); wcex.hCursor        = LoadCursor(NULL, IDC_ARROW); wcex.hbrBackground  = (HBRUSH)(COLOR_WINDOW+1); wcex.lpszMenuName   = NULL; wcex.lpszClassName  = szWindowClass; wcex.hIconSm        = LoadIcon(wcex.hInstance, MAKEINTRESOURCE(IDI_APPLICATION)); if (!RegisterClassEx(&wcex)) { MessageBox(NULL, _T("Call to RegisterClassEx failed!"), _T("Win32 Guided Tour"), NULL); return 1; } hInst = hInstance; // Store instance handle in our global variable // The parameters to CreateWindow explained: // szWindowClass: the name of the application // szTitle: the text that appears in the title bar // WS_OVERLAPPEDWINDOW: the type of window to create // CW_USEDEFAULT, CW_USEDEFAULT: initial position (x, y) // 500, 100: initial size (width, length) // NULL: the parent of this window // NULL: this application dows not have a menu bar // hInstance: the first parameter from WinMain // NULL: not used in this application HWND hWnd = CreateWindow( szWindowClass, szTitle, WS_OVERLAPPEDWINDOW, CW_USEDEFAULT, CW_USEDEFAULT, 500, 100, NULL, NULL, hInstance, NULL ); if (!hWnd) { MessageBox(NULL, _T("Call to CreateWindow failed!"), _T("Win32 Guided Tour"), NULL); return 1; } // The parameters to ShowWindow explained: // hWnd: the value returned from CreateWindow // nCmdShow: the fourth parameter from WinMain ShowWindow(hWnd, nCmdShow); UpdateWindow(hWnd); // Main message loop: MSG msg; while (GetMessage(&msg, NULL, 0, 0)) { TranslateMessage(&msg); DispatchMessage(&msg); } return (int) msg.wParam; }  
    ```  
  
### 向 WndProc 函数添加功能  
  
1.  若要启用 `WndProc` 函数以处理应用程序收到的消息，请实现 switch 语句。  
  
     处理的第一条消息是 [WM\_PAINT](http://msdn.microsoft.com/library/windows/desktop/dd145213) 消息。 应用程序收到此消息，此时必须更新其显示窗口的一部分。 （第一次显示窗口时，必须更新整个窗口。）  
  
     要处理 `WM_PAINT` 消息，首先应调用 [BeginPaint](http://msdn.microsoft.com/library/windows/desktop/dd183362)，然后处理所有的逻辑以在窗口中布局文本、按钮和其他控件，然后调用 [EndPaint](http://msdn.microsoft.com/library/windows/desktop/dd162598)。 对于此应用程序，开始调用和结束调用之间的逻辑是在窗口中显示字符串 “Hello，World\!”。 在以下代码中，请注意 [TextOut](http://msdn.microsoft.com/library/windows/desktop/dd145133) 函数用于显示字符串。  
  
    ```  
    PAINTSTRUCT ps; HDC hdc; TCHAR greeting[] = _T("Hello, World!"); switch (message) { case WM_PAINT: hdc = BeginPaint(hWnd, &ps); // Here your application is laid out. // For this introduction, we just print out "Hello, World!" // in the top left corner. TextOut(hdc, 5, 5, greeting, _tcslen(greeting)); // End application-specific layout section. EndPaint(hWnd, &ps); break; }  
    ```  
  
2.  应用程序通常会处理许多其他消息，例如 [WM\_CREATE](http://msdn.microsoft.com/library/windows/desktop/ms632619) 和 [WM\_DESTROY](http://msdn.microsoft.com/library/windows/desktop/ms632620)。 以下代码显示基本但完整的 `WndProc` 函数。  
  
    ```  
    LRESULT CALLBACK WndProc(HWND hWnd, UINT message, WPARAM wParam, LPARAM lParam) { PAINTSTRUCT ps; HDC hdc; TCHAR greeting[] = _T("Hello, World!"); switch (message) { case WM_PAINT: hdc = BeginPaint(hWnd, &ps); // Here your application is laid out. // For this introduction, we just print out "Hello, World!" // in the top left corner. TextOut(hdc, 5, 5, greeting, _tcslen(greeting)); // End application specific layout section. EndPaint(hWnd, &ps); break; case WM_DESTROY: PostQuitMessage(0); break; default: return DefWindowProc(hWnd, message, wParam, lParam); break; } return 0; }  
    ```  
  
##  <a name="example"></a> 示例  
  
#### 生成此示例  
  
1.  按照本演练前面部分介绍的“创建基于 Win32 的项目”方法创建基于 Win32 的项目。  
  
2.  按照以下步骤复制代码，然后将其粘贴在 GT\_HelloWorldWin32.cpp 源文件中。  
  
3.  在**“生成”**菜单上，单击**“生成解决方案”**。  
  
4.  按 F5 运行该应用程序。 显示屏左上角会出现包含“Hello World\!” 文字的窗口。  
  
### 代码  
  
```  
// GT_HelloWorldWin32.cpp // compile with: /D_UNICODE /DUNICODE /DWIN32 /D_WINDOWS /c #include <windows.h> #include <stdlib.h> #include <string.h> #include <tchar.h> // Global variables // The main window class name. static TCHAR szWindowClass[] = _T("win32app"); // The string that appears in the application's title bar. static TCHAR szTitle[] = _T("Win32 Guided Tour Application"); HINSTANCE hInst; // Forward declarations of functions included in this code module: LRESULT CALLBACK WndProc(HWND, UINT, WPARAM, LPARAM); int WINAPI WinMain(HINSTANCE hInstance, HINSTANCE hPrevInstance, LPSTR lpCmdLine, int nCmdShow) { WNDCLASSEX wcex; wcex.cbSize = sizeof(WNDCLASSEX); wcex.style          = CS_HREDRAW | CS_VREDRAW; wcex.lpfnWndProc    = WndProc; wcex.cbClsExtra     = 0; wcex.cbWndExtra     = 0; wcex.hInstance      = hInstance; wcex.hIcon          = LoadIcon(hInstance, MAKEINTRESOURCE(IDI_APPLICATION)); wcex.hCursor        = LoadCursor(NULL, IDC_ARROW); wcex.hbrBackground  = (HBRUSH)(COLOR_WINDOW+1); wcex.lpszMenuName   = NULL; wcex.lpszClassName  = szWindowClass; wcex.hIconSm        = LoadIcon(wcex.hInstance, MAKEINTRESOURCE(IDI_APPLICATION)); if (!RegisterClassEx(&wcex)) { MessageBox(NULL, _T("Call to RegisterClassEx failed!"), _T("Win32 Guided Tour"), NULL); return 1; } hInst = hInstance; // Store instance handle in our global variable // The parameters to CreateWindow explained: // szWindowClass: the name of the application // szTitle: the text that appears in the title bar // WS_OVERLAPPEDWINDOW: the type of window to create // CW_USEDEFAULT, CW_USEDEFAULT: initial position (x, y) // 500, 100: initial size (width, length) // NULL: the parent of this window // NULL: this application does not have a menu bar // hInstance: the first parameter from WinMain // NULL: not used in this application HWND hWnd = CreateWindow( szWindowClass, szTitle, WS_OVERLAPPEDWINDOW, CW_USEDEFAULT, CW_USEDEFAULT, 500, 100, NULL, NULL, hInstance, NULL ); if (!hWnd) { MessageBox(NULL, _T("Call to CreateWindow failed!"), _T("Win32 Guided Tour"), NULL); return 1; } // The parameters to ShowWindow explained: // hWnd: the value returned from CreateWindow // nCmdShow: the fourth parameter from WinMain ShowWindow(hWnd, nCmdShow); UpdateWindow(hWnd); // Main message loop: MSG msg; while (GetMessage(&msg, NULL, 0, 0)) { TranslateMessage(&msg); DispatchMessage(&msg); } return (int) msg.wParam; } // //  FUNCTION: WndProc(HWND, UINT, WPARAM, LPARAM) // //  PURPOSE:  Processes messages for the main window. // //  WM_PAINT    - Paint the main window //  WM_DESTROY  - post a quit message and return // // LRESULT CALLBACK WndProc(HWND hWnd, UINT message, WPARAM wParam, LPARAM lParam) { PAINTSTRUCT ps; HDC hdc; TCHAR greeting[] = _T("Hello, World!"); switch (message) { case WM_PAINT: hdc = BeginPaint(hWnd, &ps); // Here your application is laid out. // For this introduction, we just print out "Hello, World!" // in the top left corner. TextOut(hdc, 5, 5, greeting, _tcslen(greeting)); // End application-specific layout section. EndPaint(hWnd, &ps); break; case WM_DESTROY: PostQuitMessage(0); break; default: return DefWindowProc(hWnd, message, wParam, lParam); break; } return 0; }  
```  
  
## 请参阅  
 [Windows 桌面应用程序](../windows/windows-desktop-applications-cpp.md)