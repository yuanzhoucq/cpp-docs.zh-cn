---
title: 在规则 MFC Dll 中使用数据库、 OLE 和套接字 MFC 扩展 Dll
ms.date: 11/04/2016
helpviewer_keywords:
- DLLs [C++], initializing
- DLLs [C++], extension
- DLLs [C++], regular
ms.assetid: 9f1d14a7-9e2a-4760-b3b6-db014fcdb7ff
ms.openlocfilehash: d08822a04abe5a01883ad8aa1bd6d94269e810cc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62314684"
---
# <a name="using-database-ole-and-sockets-mfc-extension-dlls-in-regular-mfc-dlls"></a>在规则 MFC Dll 中使用数据库、 OLE 和套接字 MFC 扩展 Dll

当使用的 MFC 扩展 DLL 规则 MFC DLL，如果 MFC 扩展 DLL 不连接到**CDynLinkLibrary**对象链的规则 MFC DLL，则可能会遇到一个或多个一组相关的问题。 因为调试版本的 MFC 数据库、 OLE 和套接字支持 Dll 作为 MFC 扩展 Dll 实现的可能会看到类似的问题，如果你正在使用这些 MFC 功能，即使你未显式使用任何你自己的 MFC 扩展 Dll。 一些症状是：

- 当尝试反序列化的类类型的对象定义 MFC 扩展 DLL，该消息中"警告：无法加载 CYourClass 从存档。 类未定义的。" 显示在跟踪调试窗口和对象进行序列化将失败。

- 可能会引发异常，指出不好的类。

- MFC 扩展 DLL 中存储的资源无法加载，因为`AfxFindResourceHandle`将返回**NULL**或不正确的资源句柄。

- `DllGetClassObject``DllCanUnloadNow`，并`UpdateRegistry`， `Revoke`， `RevokeAll`，并`RegisterAll`成员函数的`COleObjectFactory`无法找到在 MFC 扩展 DLL 中定义的类工厂。

- `AfxDoForAllClasses` 不适用于 MFC 扩展 DLL 中的任何类。

- 标准 MFC 数据库、 套接字或 OLE 资源加载失败。 例如， **AfxLoadString**(**AFX_IDP_SQL_CONNECT_FAIL**) 返回空字符串，即使在规则 MFC DLL 正确使用 MFC 数据库类时。

这些问题的解决方案是创建和导出在 MFC 扩展 DLL 创建一个初始化函数**CDynLinkLibrary**对象。 一次性从每个规则 MFC DLL，它使用 MFC 扩展 DLL，请调用此初始化函数。

## <a name="mfc-ole-mfc-database-or-dao-or-mfc-sockets-support"></a>MFC OLE，MFC 数据库 （或 DAO），还是使用 MFC 套接字支持

如果您使用任何 MFC OLE，MFC 数据库 （或 DAO），或 MFC 套接字支持在规则 MFC DLL，分别，MFC 调试 MFC 扩展 Dll MFCOxxD.dll、 MFCDxxD.dll 和 MFCNxxD.dll （其中 xx 是版本号） 会自动链接。 为每个使用这些 Dll，必须调用预定义的初始化函数。

有关数据库支持，将调用添加到`AfxDbInitModule`规则 MFC dll 的`CWinApp::InitInstance`函数。 请确保此调用之前的任何基类调用或任何添加的代码访问 MFCDxxD.dll。 此函数不带任何参数，并返回 void。

对于 OLE 支持添加到调用`AfxOleInitModule`规则 MFC dll 的`CWinApp::InitInstance`。 请注意， **COleControlModule InitInstance**函数调用`AfxOleInitModule`，因此，如果你要构建 OLE 控件并将使用`COleControlModule`，不应将添加到此调用`AfxOleInitModule`。

有关套接字支持，将调用添加到`AfxNetInitModule`规则 MFC dll 的`CWinApp::InitInstance`。

请注意，MFC Dll 的发行版本和应用程序数据库，套接字，不使用单独的 Dll 或 OLE 支持。 但是，它是安全地在发布模式下调用这些函数的初始化。

## <a name="cdynlinklibrary-objects"></a>CDynLinkLibrary 对象

在每个操作在本主题开头所述，MFC 需要进行搜索所需的值或对象。 例如，在反序列化，MFC 需要的所有当前可用运行时类以匹配档案，并将其适当的运行时类中的对象中进行搜索。

这些搜索的一部分，MFC 通过扫描中使用的所有 MFC 扩展 Dll 链的每个步骤**CDynLinkLibrary**对象。 **CDynLinkLibrary**对象将附加自动链接到在其构造过程中和创建的每个 MFC 扩展 DLL 又在初始化过程。 此外，（应用程序或规则 MFC DLL） 的每个模块具有其自己的链**CDynLinkLibrary**对象。

对 MFC 扩展 DLL，若要连接到**CDynLinkLibrary**链，它必须创建**CDynLinkLibrary**使用 MFC 扩展 DLL 的每个模块的上下文中的对象。 因此，如果 MFC 扩展 DLL 将用于从 MFC 的规则 Dll，它必须提供创建的导出的初始化函数**CDynLinkLibrary**对象。 每个规则 MFC DLL，使用 MFC 扩展 DLL 必须调用导出的初始化函数。

如果 MFC 扩展 DLL 只会将用于从 MFC 应用程序 (.exe) 和永远不会从规则 MFC DLL，则只需创建**CDynLinkLibrary**对象中的 MFC 扩展 DLL `DllMain`。 这是 MFC DLL 向导 MFC 扩展 DLL 代码的用途。 隐式地加载 MFC 扩展 DLL 时`DllMain`加载并执行应用程序不断启动之前。 任何**CDynLinkLibrary**作品都连接到默认链 MFC DLL 保留为 MFC 应用程序。

请注意，它是一个好主意有多个**CDynLinkLibrary**尤其是 MFC 扩展 DLL 将从内存中动态地卸载任何一个链中的一个 MFC 扩展 DLL 中的对象。 请勿调用初始化函数不止一次从任何一个模块。

## <a name="sample-code"></a>代码示例

此示例代码假定将隐式将规则 MFC DLL 链接到 MFC 扩展 DLL。 通过构建规则 MFC DLL 时链接到 MFC 扩展 DLL 的导入库 (.lib) 完成此操作。

MFC 扩展 DLL 在源中应为以下行：

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

请务必导出**InitYourExtDLL**函数。 这可以通过使用 **__declspec （dllexport)** 或 DLL 的.def 文件，如下所示：

```
// YourExtDLL.Def:
LIBRARY      YOUREXTDLL
CODE         PRELOAD MOVEABLE DISCARDABLE
DATA         PRELOAD SINGLE
EXPORTS
    InitYourExtDLL
```

添加对的调用`InitInstance`的成员`CWinApp`-派生的对象中每个使用 MFC 扩展 DLL 的规则 MFC DLL:

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

- [初始化 MFC 扩展 DLL](run-time-library-behavior.md#initializing-extension-dlls)

- [初始化规则 MFC Dll](run-time-library-behavior.md#initializing-regular-dlls)

### <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？

- [MFC 扩展 DLL](extension-dlls.md)

- [静态链接到 MFC 的规则 MFC DLL](regular-dlls-statically-linked-to-mfc.md)

- [动态链接到 MFC 的规则 MFC DLL](regular-dlls-dynamically-linked-to-mfc.md)

- [将 MFC 作为 DLL 的一部分使用](../mfc/tn011-using-mfc-as-part-of-a-dll.md)

- [MFC 的 DLL 版本](../mfc/tn033-dll-version-of-mfc.md)

## <a name="see-also"></a>请参阅

[MFC 扩展 DLL](extension-dlls.md)
