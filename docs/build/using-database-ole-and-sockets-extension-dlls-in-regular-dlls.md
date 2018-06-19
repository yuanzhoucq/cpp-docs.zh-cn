---
title: 在 MFC 的规则 Dll 中使用数据库、 OLE 和套接字 MFC 扩展 Dll |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DLLs [C++], initializing
- DLLs [C++], extension
- DLLs [C++], regular
ms.assetid: 9f1d14a7-9e2a-4760-b3b6-db014fcdb7ff
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f902f3b512b5684cf185829fdf4346b8851ff8ba
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32391400"
---
# <a name="using-database-ole-and-sockets-mfc-extension-dlls-in-regular-mfc-dlls"></a>在 MFC 的规则 Dll 中使用数据库、 OLE 和套接字 MFC 扩展 Dll
在使用 MFC 扩展 DLL 从正则 MFC DLL，如果 MFC 扩展 DLL 不连接到**CDynLinkLibrary**对象链的常规 MFC DLL，则可能会遇到一个或多个对相关问题的一组。 由于支持的调试版本的 MFC 数据库、 OLE 和套接字 Dll 作为 MFC 扩展 Dll 实现，可能会看到类似的问题，如果你正在使用这些 MFC 功能，即使你未显式使用任何你自己的 MFC 扩展 Dll。 某些症状是：  
  
-   在 MFC 扩展 DLL，消息尝试反序列化的类的类型对象的定义"警告： 无法加载 CYourClass 从存档。 类未定义的。" 将显示在跟踪调试窗口和对象无法序列化。  
  
-   可能引发一个异常，指示不好的类。  
  
-   MFC 扩展 DLL 中存储的资源无法加载，因为`AfxFindResourceHandle`返回**NULL**或不正确的资源句柄。  
  
-   `DllGetClassObject``DllCanUnloadNow`，和`UpdateRegistry`， `Revoke`， `RevokeAll`，和`RegisterAll`的成员函数`COleObjectFactory`无法找到在 MFC 扩展 DLL 中定义的类工厂。  
  
-   `AfxDoForAllClasses` 不适合在 MFC 扩展 DLL 中的任何类。  
  
-   标准 MFC 数据库、 套接字或 OLE 资源加载失败。 例如， **AfxLoadString**(**AFX_IDP_SQL_CONNECT_FAIL**) 返回空字符串，即使是在正则 MFC DLL 正确使用 MFC 数据库类。  
  
 这些问题的解决方案是创建并导出 MFC 扩展创建的 DLL 中的初始化函数**CDynLinkLibrary**对象。 完全后从每个规则的 MFC DLL，它使用 MFC 扩展 DLL，请调用此初始化函数。  
  
## <a name="mfc-ole-mfc-database-or-dao-or-mfc-sockets-support"></a>MFC OLE、 MFC 数据库 （或 DAO），或 MFC 套接字支持  
 如果你使用任何 MFC OLE、 MFC 数据库 （或 DAO），或 MFC 套接字在常规 MFC DLL，分别支持的 MFC 调试 MFC 扩展 Dll MFCOxxD.dll、 MFCDxxD.dll 和 MFCNxxD.dll （其中，xx 是版本号） 会自动链接。 必须为每个你使用这些 Dll 中调用预定义的初始化函数。  
  
 对于数据库支持，添加对的调用`AfxDbInitModule`到常规 MFC DLL`CWinApp::InitInstance`函数。 请确保此调用发生在基类中的任何调用之前或任何添加的代码访问 MFCDxxD.dll。 此函数不带任何参数，并返回 void。  
  
 有关 OLE 支持，添加对的调用`AfxOleInitModule`到常规 MFC DLL `CWinApp::InitInstance`。 请注意， **COleControlModule InitInstance**函数调用`AfxOleInitModule`已，因此，如果你要生成 OLE 控件并将`COleControlModule`，则不应添加到此调用`AfxOleInitModule`。  
  
 有关套接字支持，添加对的调用`AfxNetInitModule`到常规 MFC DLL `CWinApp::InitInstance`。  
  
 请注意，MFC Dll 的发行版本和应用程序对于数据库，套接字，不使用单独的 Dll 或 OLE 支持。 但是，它是安全地在发布模式下调用这些初始化函数。  
  
## <a name="cdynlinklibrary-objects"></a>CDynLinkLibrary 对象  
 在每个操作本主题开头所述，MFC 需要进行搜索所需的值或对象。 例如，在反序列化期间 MFC 需要搜索所有当前可用的运行时类以匹配在档案，并将其正确的运行时类的对象。  
  
 作为这些搜索的一部分，MFC 通过扫描中使用的所有 MFC 扩展 Dll 通过遍历链**CDynLinkLibrary**对象。 **CDynLinkLibrary**对象将附加自动链接到在其构造过程并且通过创建每个 MFC 扩展 DLL 反过来在初始化过程。 此外，每个模块 （应用程序或常规 MFC DLL） 具有其自己的链**CDynLinkLibrary**对象。  
  
 有关 MFC 扩展 DLL，若要连接到**CDynLinkLibrary**链，它必须创建**CDynLinkLibrary**使用 MFC 扩展 DLL 每个模块的上下文中的对象。 因此，如果 MFC 扩展 DLL 将用于从 MFC 的规则 Dll，它必须提供一个导出的初始化函数，创建**CDynLinkLibrary**对象。 每个规则的 MFC DLL，使用 MFC 扩展 DLL 必须调用导出的初始化函数。  
  
 如果 MFC 扩展 DLL 只会将用于从 MFC 应用程序 (.exe) 和永远不会从正则 MFC DLL，则只需创建**CDynLinkLibrary**对象中的 MFC 扩展 DLL `DllMain`。 这是 MFC DLL 向导 MFC 扩展 DLL 代码的。 隐式加载 MFC 扩展 DLL 时`DllMain`加载并执行应用程序启动之前。 任何**CDynLinkLibrary**创建有线到默认链 MFC DLL 保留为 MFC 应用程序。  
  
 请注意，它是一个好办法有多个**CDynLinkLibrary**尤其是 MFC 扩展 DLL 将动态从内存中卸载任何一个链中的一个 MFC 扩展 DLL 中的对象。 请勿调用初始化函数不止一次从任何一个模块。  
  
## <a name="sample-code"></a>代码示例  
 此代码示例假定常规 MFC DLL 隐式链接到 MFC 扩展 DLL。 这是通过时生成正则 MFC DLL 链接到 MFC 扩展 DLL 导入库 (.lib) 实现的。  
  
 源中的 MFC 扩展 DLL 应为以下行：  
  
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
        // MFC extension DLL one-time initialization  
        if (!AfxInitExtensionModule(extensionDLL, hInstance))  
           return 0;  
    }  
    return 1;   // ok  
}  
  
// Exported DLL initialization is run in context of  
// application or regular MFC DLL  
extern "C" void WINAPI InitYourExtDLL()  
{  
    // create a new CDynLinkLibrary for this app  
    new CDynLinkLibrary(extensionDLL);  
  
    // add other initialization here  
}  
```  
  
 请务必导出**InitYourExtDLL**函数。 这可以使用 **__declspec （dllexport)** 或，如下所示的 DLL 的.def 文件中：  
  
```  
// YourExtDLL.Def:  
LIBRARY      YOUREXTDLL  
CODE         PRELOAD MOVEABLE DISCARDABLE  
DATA         PRELOAD SINGLE  
EXPORTS  
    InitYourExtDLL  
```  
  
 添加对的调用`InitInstance`的成员`CWinApp`-派生对象中每个规则使用 MFC 扩展 DLL 的 MFC DLL:  
  
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
    TRACE0("YOUR regular MFC DLL initializing\n");  
  
    // wire any MFC extension DLLs into CDynLinkLibrary chain  
    InitYourExtDLL();  
  
    return TRUE;  
}  
```  
  
### <a name="what-do-you-want-to-do"></a>你希望做什么？  
  
-   [初始化 MFC 扩展 DLL](../build/run-time-library-behavior.md#initializing-extension-dlls)  
  
-   [初始化 MFC 的规则 Dll](../build/run-time-library-behavior.md#initializing-regular-dlls)  
  
### <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？  
  
-   [MFC 扩展 DLL](../build/extension-dlls.md)  
  
-   [静态链接到 MFC 的规则 MFC DLL](../build/regular-dlls-statically-linked-to-mfc.md)  
  
-   [动态链接到 MFC 的规则 MFC DLL](../build/regular-dlls-dynamically-linked-to-mfc.md)  
  
-   [将 MFC 作为 DLL 的一部分使用](../mfc/tn011-using-mfc-as-part-of-a-dll.md)  
  
-   [MFC 的 DLL 版本](../mfc/tn033-dll-version-of-mfc.md)  
  
## <a name="see-also"></a>请参阅  
 [MFC 扩展 DLL](../build/extension-dlls.md)