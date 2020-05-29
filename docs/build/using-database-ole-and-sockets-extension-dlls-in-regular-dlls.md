---
title: 在规则 MFC DLL 中使用数据库、OLE 和套接字 MFC 扩展 DLL
ms.date: 11/04/2016
helpviewer_keywords:
- DLLs [C++], initializing
- DLLs [C++], extension
- DLLs [C++], regular
ms.assetid: 9f1d14a7-9e2a-4760-b3b6-db014fcdb7ff
ms.openlocfilehash: d08822a04abe5a01883ad8aa1bd6d94269e810cc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62314684"
---
# <a name="using-database-ole-and-sockets-mfc-extension-dlls-in-regular-mfc-dlls"></a>在规则 MFC DLL 中使用数据库、OLE 和套接字 MFC 扩展 DLL

从规则 MFC DLL 使用 MFC 扩展 DLL 时，如果 MFC 扩展 DLL 未连接到规则 MFC DLL 的 CDynLinkLibrary  对象链中，则可能会遇到一组相关问题中的一个或多个问题。 由于 MFC 数据库、OLE 和套接字支持 DLL 的调试版本是以 MFC 扩展 DLL 的形式实现，因此，如果你使用这些 MFC 功能，即使未显式使用你自己的任何 MFC 扩展 DLL，也可能会遇到类似问题。 一些症状如下：

- 尝试反序列化 MFC 扩展 DLL 中定义的类类型的对象时，消息“警告:无法从存档加载 CYourClass。 类未定义。” 出现在跟踪调试窗口中，对象无法序列化。

- 可能会引发指示类错误的异常。

- 由于 `AfxFindResourceHandle` 返回 NULL  或不正确的资源句柄，因此存储在 MFC 扩展 DLL 中的资源无法加载。

- `DllGetClassObject`、`DllCanUnloadNow` 以及 `RegisterAll` 的 `UpdateRegistry`、`Revoke`、`RevokeAll` 和 `COleObjectFactory` 成员函数无法找到在 MFC 扩展 DLL 中定义的类工厂。

- `AfxDoForAllClasses` 不适用于 MFC 扩展 DLL 中的任何类。

- 标准 MFC 数据库、套接字或 OLE 资源无法加载。 例如，AfxLoadString  (AFX_IDP_SQL_CONNECT_FAIL  ) 返回空字符串，即使在规则 MFC DLL 正确使用 MFC 数据库类时也是如此。

这些问题的解决方案是在 MFC 扩展 DLL 中创建和导出用于创建 CDynLinkLibrary  对象的初始化函数。 从每个使用 MFC 扩展 DLL 的规则 MFC DLL 恰好调用一次此初始化函数。

## <a name="mfc-ole-mfc-database-or-dao-or-mfc-sockets-support"></a>MFC OLE、MFC 数据库（或 DAO）或是 MFC 套接字支持

如果在规则 MFC DLL 中使用任何 MFC OLE、MFC 数据库（或 DAO）或是 MFC 套接字支持，则会自动地分别链接 MFC 调试 MFC 扩展 DLL MFCOxxD.dll、MFCDxxD.dll 和 MFCNxxD.dll（其中 xx 是版本号）。 必须为所使用的每个 DLL 调用预定义初始化函数。

对于数据库支持，将对 `AfxDbInitModule` 的调用添加到规则 MFC DLL 的 `CWinApp::InitInstance` 函数中。 确保在任何基类调用或任何访问 MFCDxxD.dll 的已添加代码之前进行此调用。 此函数不采用任何参数并返回 void。

对于 OLE 支持，将对 `AfxOleInitModule` 的调用添加到规则 MFC DLL 的 `CWinApp::InitInstance` 中。 请注意，COleControlModule InitInstance  函数已调用 `AfxOleInitModule`，因此如果要生成 OLE 控件并使用 `COleControlModule`，则不应将此调用添加到 `AfxOleInitModule`。

对于套接字支持，将对 `AfxNetInitModule` 的调用添加到规则 MFC DLL 的 `CWinApp::InitInstance` 中。

请注意，MFC DLL 和应用程序的发布版本不将单独的 DLL 用于数据库、套接字或 OLE 支持。 但是，在发布模式下可安全地调用这些初始化函数。

## <a name="cdynlinklibrary-objects"></a>CDynLinkLibrary 对象

在本主题开头提到的每个操作期间，MFC 都需要搜索所需值或对象。 例如，在反序列化期间，MFC 需要搜索所有当前可用的运行时类，以使存档中的对象与其适当的运行时类匹配。

作为这些搜索的一部分，MFC 通过遍历 CDynLinkLibrary  对象链来扫描所使用的所有 MFC 扩展 DLL。 CDynLinkLibrary  对象在其构造过程中会自动附加到一个链，并在初始化过程中依次由每个 MFC 扩展 DLL 创建。 此外，每个模块（应用程序或规则 MFC DLL）都有自己的 CDynLinkLibrary  对象链。

若要使 MFC 扩展 DLL 连接到 CDynLinkLibrary  链中，它必须在使用 MFC 扩展 DLL 的每个模块的上下文中创建一个 CDynLinkLibrary  对象。 因此，如果要从规则 MFC DLL 使用 MFC 扩展 DLL，则它必须提供用于创建 CDynLinkLibrary  对象的导出初始化函数。 每个使用 MFC 扩展 DLL 的规则 MFC DLL 都必须调用导出初始化函数。

如果只是要从 MFC 应用程序 (.exe) 使用 MFC 扩展 DLL，而绝不会从规则 MFC DLL 进行使用，则只需在 MFC 扩展 DLL 的 `DllMain` 中创建 CDynLinkLibrary  对象即可。 这是 MFC DLL 向导 MFC 扩展 DLL 代码所执行的操作。 隐式加载 MFC 扩展 DLL 时，`DllMain` 会在应用程序启动之前加载并执行。 任何 CDynLinkLibrary  创建都会连接到 MFC DLL 为 MFC 应用程序保留的默认链中。

请注意，在任何一个链中具有多个来自一个 MFC 扩展 DLL 的 CDynLinkLibrary  对象是个坏主意，尤其是在 MFC 扩展 DLL 将从内存中动态卸载时。 请不要从任何一个模块多次调用初始化函数。

## <a name="sample-code"></a>代码示例

此代码示例假设规则 MFC DLL 隐式链接到 MFC 扩展 DLL。 这通过在生成规则 MFC DLL 时链接到 MFC 扩展 DLL 的导入库 (.lib) 来实现。

以下行应在 MFC 扩展 DLL 的源代码中：

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

确保导出 InitYourExtDLL  函数。 可以使用 __declspec(dllexport)  或是在 DLL 的 .def 文件中完成此操作，如下所示：

```
// YourExtDLL.Def:
LIBRARY      YOUREXTDLL
CODE         PRELOAD MOVEABLE DISCARDABLE
DATA         PRELOAD SINGLE
EXPORTS
    InitYourExtDLL
```

使用 MFC 扩展 DLL 在每个规则 MFC DLL 中添加对 `CWinApp` 派生对象的 `InitInstance` 成员的调用：

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

- [初始化规则 MFC DLL](run-time-library-behavior.md#initializing-regular-dlls)

### <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？

- [MFC 扩展 DLL](extension-dlls.md)

- [静态链接到 MFC 的规则 MFC DLL](regular-dlls-statically-linked-to-mfc.md)

- [动态链接到 MFC 的规则 MFC DLL](regular-dlls-dynamically-linked-to-mfc.md)

- [将 MFC 用作 DLL 的一部分](../mfc/tn011-using-mfc-as-part-of-a-dll.md)

- [MFC 的 DLL 版本](../mfc/tn033-dll-version-of-mfc.md)

## <a name="see-also"></a>请参阅

[MFC 扩展 DLL](extension-dlls.md)
