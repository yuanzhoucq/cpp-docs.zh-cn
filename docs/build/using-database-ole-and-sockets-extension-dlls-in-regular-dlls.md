---
title: "在规则 DLL 中使用数据库、OLE 和套接字扩展 DLL | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DLL [C++], 扩展"
  - "DLL [C++], 初始化"
  - "DLL [C++], 规则"
ms.assetid: 9f1d14a7-9e2a-4760-b3b6-db014fcdb7ff
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 在规则 DLL 中使用数据库、OLE 和套接字扩展 DLL
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

从规则 DLL 中使用扩展 DLL 时，如果扩展 DLL 没有连到规则 DLL 的 **CDynLinkLibrary** 对象链中，可能会碰到一组相关问题中的一个或多个。  由于 MFC 数据库、OLE 和套接字支持 DLL 的调试版本是以扩展 DLL 的形式实现的，因此，即使您没有显式使用任何自己的扩展 DLL，使用这些 MFC 功能时也可能碰到类似的问题。  问题的某些表现是：  
  
-   当尝试反序列化其类型为扩展 DLL 中定义的类的对象时，“跟踪”调试窗口中将出现“警告：无法从存档加载 CYourClass。  类未定义。”消息，并且该对象的序列化会失败。  
  
-   可能会引发指示“错误的类”的异常。  
  
-   由于 `AfxFindResourceHandle` 返回 **NULL** 或不正确的资源句柄，存储在扩展 DLL 中的资源未能加载。  
  
-   `DllGetClassObject`、`DllCanUnloadNow` 和 `COleObjectFactory` 的 `UpdateRegistry`、`Revoke`、`RevokeAll` 和 `RegisterAll` 成员函数未能定位扩展 DLL 中定义的类工厂。  
  
-   `AfxDoForAllClasses` 对扩展 DLL 中的所有类都无效。  
  
-   标准 MFC 数据库、套接字或 OLE 资源未能加载。  例如，即使规则 DLL 正确使用了 MFC 数据库类，**AfxLoadString**\(**AFX\_IDP\_SQL\_CONNECT\_FAIL**\) 仍返回空字符串。  
  
 解决这些问题的方法是在扩展 DLL 中创建和导出一个创建 **CDynLinkLibrary** 对象的初始化函数。  从使用扩展 DLL 的每个规则 DLL 中调用此初始化函数的次数不应超过一次。  
  
## MFC OLE、MFC 数据库（或 DAO）或 MFC 套接字支持  
 如果在规则 DLL 中使用了任何 MFC OLE、MFC 数据库（或 DAO）或 MFC 套接字支持，则将分别自动链接 MFC 调试扩展 DLL MFCOxxD.dll、MFCDxxD.dll 和 MFCNxxD.dll（其中 xx 是版本号）。  必须为正在使用的上述每个 DLL 调用预定义的初始化函数。  
  
 对于数据库支持，在规则 DLL 的 `CWinApp::InitInstance` 函数中添加 `AfxDbInitModule` 调用。  确保此调用在任何基类调用或任何添加用来访问 MFCDxxD.dll 的代码之前发生。  此函数不采用任何参数且返回 void。  
  
 对于 OLE 支持，在规则 DLL 的 `CWinApp::InitInstance` 中添加 `AfxOleInitModule` 调用。  请注意，**COleControlModule InitInstance** 函数已经调用 `AfxOleInitModule`，因此如果要生成 OLE 控件并使用 `COleControlModule`，则不应添加此 `AfxOleInitModule` 调用。  
  
 对于套接字支持，在规则 DLL 的 `CWinApp::InitInstance` 中添加 `AfxNetInitModule` 调用。  
  
 请注意，MFC DLL 和应用程序的发布版本不对数据库、套接字或 OLE 支持使用单独的 DLL。  不过，以发布模式调用这些初始化函数是安全的。  
  
## CDynLinkLibrary 对象  
 在本主题的开头提到的每个操作期间，MFC 都需要搜索所需的值或对象。  例如，在反序列化期间，MFC 需要仔细搜索所有当前可用的运行时类，以将存档中的对象与它们的正确运行时类进行匹配。  
  
 作为这些搜索的一部分，MFC 通过浏览 **CDynLinkLibrary** 对象链，扫描所有正在使用的扩展 DLL。  **CDynLinkLibrary** 对象在构造期间自动附加到某个链上，并在初始化期间由每个扩展 DLL 轮流创建。  另外，每个模块（应用程序或规则 DLL）均具有自己的 **CDynLinkLibrary** 对象链。  
  
 对于扩展 DLL 而言，要想连到 **CDynLinkLibrary** 链中，必须在使用扩展 DLL 的每个模块的上下文中创建一个 **CDynLinkLibrary** 对象。  因此，如果要从规则 DLL 中使用扩展 DLL，扩展 DLL 必须提供一个创建 **CDynLinkLibrary** 对象的导出初始化函数。  每个使用扩展 DLL 的规则 DLL 都必须调用此导出初始化函数。  
  
 如果只是从 MFC 应用程序 \(.exe\) 中而决不从规则 DLL 中使用扩展 DLL，则只需在扩展 DLL 的 `DllMain` 中创建 **CDynLinkLibrary** 对象即可。  这就是“MFC DLL 向导”扩展 DLL 代码所执行的操作。  隐式加载扩展 DLL 时，`DllMain` 在应用程序启动前加载并执行。  所有 **CDynLinkLibrary** 创建都连到 MFC DLL 为 MFC 应用程序保留的默认链中。  
  
 请注意，在任何一个链中，来自一个扩展 DLL 的 **CDynLinkLibrary** 对象都不应超过一个，特别是当扩展 DLL 将从内存动态卸载时。  从任何一个模块中调用初始化函数的次数不应超过一次。  
  
## 代码示例  
 此代码示例假设规则 DLL 隐式链接到扩展 DLL。  这是通过在生成规则 DLL 时链接到扩展 DLL 的导入库 \(.lib\) 得以实现的。  
  
 以下行应在扩展 DLL 的源中：  
  
```  
// YourExtDLL.cpp:  
  
// standard MFC extension DLL routines  
#include "afxdllx.h"  
  
static AFX_EXTENSION_MODULE NEAR extensionDLL = { NULL, NULL };  
  
extern "C" int APIENTRY  
DllMain(HINSTANCE hInstance, DWORD dwReason, LPVOID lpReserved)  
{  
    if (dwReason == DLL_PROCESS_ATTACH)  
    {  
        // extension DLL one-time initialization  
        if (!AfxInitExtensionModule(extensionDLL, hInstance))  
           return 0;  
    }  
    return 1;   // ok  
}  
  
// Exported DLL initialization is run in context of  
// application or regular DLL  
extern "C" void WINAPI InitYourExtDLL()  
{  
    // create a new CDynLinkLibrary for this app  
    new CDynLinkLibrary(extensionDLL);  
  
    // add other initialization here  
}  
```  
  
 务必要导出 **InitYourExtDLL** 函数。  可以通过使用 **\_\_declspec\(dllexport\)** 来完成此操作，或按如下所示在 DLL 的 .def 文件中完成：  
  
```  
// YourExtDLL.Def:  
LIBRARY      YOUREXTDLL  
CODE         PRELOAD MOVEABLE DISCARDABLE  
DATA         PRELOAD SINGLE  
EXPORTS  
    InitYourExtDLL  
```  
  
 在使用扩展 DLL 的每个规则 DLL 中，添加 `CWinApp` 派生对象的 `InitInstance` 成员调用：  
  
```  
// YourRegularDLL.cpp:  
  
class CYourRegularDLL : public CWinApp  
{  
public:  
    virtual BOOL InitInstance(); // Initialization  
    virtual int ExitInstance();  // Termination  
  
    // nothing special for the constructor  
    CYourRegularDLL(LPCTSTR pszAppName) : CWinApp(pszAppName) { }  
};  
  
BOOL CYourRegularDLL::InitInstance()  
{  
    // any DLL initialization goes here  
    TRACE0("YOUR regular DLL initializing\n");  
  
    // wire any extension DLLs into CDynLinkLibrary chain  
    InitYourExtDLL();  
  
    return TRUE;  
}  
```  
  
### 你希望做什么？  
  
-   [初始化扩展 DLL](../build/initializing-extension-dlls.md)  
  
-   [初始化规则 DLL](../build/initializing-regular-dlls.md)  
  
### 您想进一步了解什么？  
  
-   [扩展 DLL](../build/extension-dlls.md)  
  
-   [静态链接到 MFC 的规则 DLL](../build/regular-dlls-statically-linked-to-mfc.md)  
  
-   [动态链接到 MFC 的规则 DLL](../build/regular-dlls-dynamically-linked-to-mfc.md)  
  
-   [将 MFC 作为 DLL 的一部分使用](../mfc/tn011-using-mfc-as-part-of-a-dll.md)  
  
-   [MFC 的 DLL 版本](../mfc/tn033-dll-version-of-mfc.md)  
  
## 请参阅  
 [扩展 DLL](../build/extension-dlls.md)