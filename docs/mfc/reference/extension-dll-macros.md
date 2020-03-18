---
title: 用于管理 Dll 的宏和函数
ms.date: 03/27/2019
helpviewer_keywords:
- module macros in MFC
ms.assetid: 303f4161-cb5e-4099-81ad-acdb11aa60fb
ms.openlocfilehash: b27f8763b60dc7ce3ee074cad1365e7e1de3a7e6
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2020
ms.locfileid: "79426695"
---
# <a name="macros-and-functions-for-managing-dlls"></a>用于管理 Dll 的宏和函数

|||
|-|-|
|[AFX_EXT_CLASS](#afx_ext_class)]|导出类。|
|[AFX_MANAGE_STATE](#afx_manage_state)|保护 DLL 中的导出函数。|
|[AfxOleInitModule](#afxoleinitmodule)|从动态链接到 MFC 的规则 MFC DLL 提供 OLE 支持。|
|[AfxNetInitModule](#afxnetinitmodule)|提供从动态链接到 MFC 的规则 MFC DLL 的 MFC 套接字支持。|
|[AfxGetAmbientActCtx](#afxgetambientactctx)|获取每个模块的状态标志的当前状态。|
|[AfxGetStaticModuleState](#afxgetstaticmodulestate)|在初始化之前设置模块状态，并/或在清理后还原以前的模块状态。|
|[AfxInitExtensionModule](#afxinitextensionmodule)|初始化 DLL。|
|[AfxSetAmbientActCtx](#afxsetambientactctx)|设置每个模块的状态标志，该标志影响 MFC 的 WinSxS 行为。|
|[AfxTermExtensionModule](#afxtermextensionmodule)|当每个进程与 DLL 分离时，允许 MFC 清除 MFC 扩展 DLL。|

## <a name="afx_ext_class"></a>AFX_EXT_CLASS

[MFC 扩展 dll](../../build/extension-dlls.md)使用宏 AFX_EXT_CLASS 来导出类;链接到 MFC 扩展 DLL 的可执行文件使用宏来导入类。

### <a name="remarks"></a>备注

使用 AFX_EXT_CLASS 宏，用于生成 MFC 扩展 DLL 的相同头文件可用于链接到 DLL 的可执行文件。

在 DLL 的标头文件中，将 AFX_EXT_CLASS 关键字添加到类的声明中，如下所示：

```cpp
class AFX_EXT_CLASS CMyClass : public CDocument
{
// <body of class>
};
```

有关详细信息，请参阅[使用 AFX_EXT_CLASS 导出和导入](../../build/exporting-and-importing-using-afx-ext-class.md)。

### <a name="requirements"></a>要求

**标头：** afxv_dll。h

## <a name="afx_manage_state"></a>AFX_MANAGE_STATE

调用此宏可保护 DLL 中的导出函数。

### <a name="syntax"></a>语法

```
AFX_MANAGE_STATE(AFX_MODULE_STATE* pModuleState )
```

### <a name="parameters"></a>parameters

*pModuleState*<br/>
指向 `AFX_MODULE_STATE` 结构的指针。

### <a name="remarks"></a>备注

调用此宏时， *pModuleState*是即时包含作用域的剩余部分的有效模块状态。 离开作用域后，将自动还原以前的有效模块状态。
`AFX_MODULE_STATE` 结构包含模块的全局数据，即推送或弹出模块状态的部分。

默认情况下，MFC 使用主应用程序的资源句柄来加载资源模板。 如果 DLL 中有一个已导出的函数，例如在 DLL 中启动对话框的函数，则该模板实际上存储在 DLL 模块中。 需要为要使用的正确句柄切换模块状态。 为此，可将以下代码添加到函数的开头：

```cpp
AFX_MANAGE_STATE(AfxGetStaticModuleState( ));
```

这会将当前模块状态替换为从[AfxGetStaticModuleState](#afxgetstaticmodulestate)返回的状态，直到当前范围结束。

有关模块状态和 MFC 的详细信息，请参阅[创建新文档、窗口和视图](../creating-new-documents-windows-and-views.md)中的 "管理 MFC 模块的状态数据" 和[技术说明 58](../tn058-mfc-module-state-implementation.md)。

> [!NOTE]
>  当 MFC 为程序集创建激活上下文时，它将使用[AfxWinInit](application-information-and-management.md#afxwininit)创建上下文并 `AFX_MANAGE_STATE` 激活和停用该上下文。 另请注意，为静态 MFC 库和 MFC Dll 启用了 `AFX_MANAGE_STATE`，以便允许在用户 DLL 所选的正确激活上下文中执行 MFC 代码。 有关详细信息，请参阅[MFC 模块状态中的激活上下文支持](../support-for-activation-contexts-in-the-mfc-module-state.md)。

### <a name="requirements"></a>要求

**标头：** afxstat_。h

## <a name="a-nameafxoleinitmodulea-afxoleinitmodule"></a><a name="afxoleinitmodule"><a/> AfxOleInitModule

若要从动态链接到 MFC 的常规 MFC DLL 中获取 OLE 支持，请在常规 MFC DLL 的 `CWinApp::InitInstance` 函数中调用此函数以初始化 MFC OLE DLL。

### <a name="syntax"></a>语法

```
void AFXAPI AfxOleInitModule( );
```

### <a name="remarks"></a>备注

MFC OLE DLL 是 MFC 扩展 DLL;为了使 MFC 扩展 DLL 能够连接到 `CDynLinkLibrary` 链，它必须在将使用它的每个模块的上下文中创建一个 `CDynLinkLibrary` 的对象。 `AfxOleInitModule` 在您的常规 MFC DLL 的上下文中创建 `CDynLinkLibrary` 对象，以便将其连接到常规 MFC DLL 的 `CDynLinkLibrary` 对象链。

如果要生成 OLE 控件并使用 `COleControlModule`，则不应调用 `AfxOleInitModule`，因为 `COleControlModule` 调用的 `InitInstance` 成员函数 `AfxOleInitModule`。

### <a name="requirements"></a>要求

**标头**： \<afxdll_ .h >

## <a name="afxnetinitmodule"></a>AfxNetInitModule

对于动态链接到 MFC 的规则 MFC DLL 的 MFC 套接字支持，请在常规 MFC DLL 的 `CWinApp::InitInstance` 函数中添加对此函数的调用，以初始化 MFC 套接字 DLL。

### <a name="syntax"></a>语法

```
void AFXAPI AfxNetInitModule( );
```

### <a name="remarks"></a>备注

MFC 套接字 DLL 是 MFC 扩展 DLL;为了使 MFC 扩展 DLL 能够连接到 `CDynLinkLibrary` 链，它必须在将使用它的每个模块的上下文中创建一个 `CDynLinkLibrary` 的对象。 `AfxNetInitModule` 在您的常规 MFC DLL 的上下文中创建 `CDynLinkLibrary` 对象，以便将其连接到常规 MFC DLL 的 `CDynLinkLibrary` 对象链。

### <a name="requirements"></a>要求

**标头：** \<afxdll_ .h >

## <a name="afxgetambientactctx"></a>AfxGetAmbientActCtx

使用此函数获取每个模块的状态标志的当前状态，这将影响 MFC 的 WinSxS 行为。

### <a name="syntax"></a>语法

```
BOOL AFXAPI AfxGetAmbientActCtx();
```

### <a name="return-value"></a>返回值

模块状态标志的当前值。

### <a name="remarks"></a>备注

如果设置了标志（这是默认设置），并且一个线程进入 MFC 模块（请参阅[AFX_MANAGE_STATE](#afx_manage_state)），则激活模块的上下文。

如果未设置该标志，则线程进入时不会激活模块的上下文。

模块的上下文从其清单确定，通常会嵌入模块资源。

### <a name="requirements"></a>要求

**标头：** afxcomctl32。h

## <a name="afxgetstaticmodulestate"></a>AfxGetStaticModuleState

调用此函数可在初始化之前设置模块状态，并/或在清理后还原以前的模块状态。

### <a name="syntax"></a>语法

```
AFX_MODULE_STATE* AFXAPI AfxGetStaticModuleState( );
```

### <a name="return-value"></a>返回值

指向 `AFX_MODULE_STATE` 结构的指针。

### <a name="remarks"></a>备注

`AFX_MODULE_STATE` 结构包含模块的全局数据，即推送或弹出模块状态的部分。

默认情况下，MFC 使用主应用程序的资源句柄来加载资源模板。 如果 DLL 中有一个已导出的函数，例如在 DLL 中启动对话框的函数，则该模板实际上存储在 DLL 模块中。 需要为要使用的正确句柄切换模块状态。 为此，可将以下代码添加到函数的开头：

```cpp
AFX_MANAGE_STATE(AfxGetStaticModuleState( ));
```

这会将当前模块状态替换为从 `AfxGetStaticModuleState` 返回的状态，直到当前范围结束。

有关模块状态和 MFC 的详细信息，请参阅[创建新文档、窗口和视图](../creating-new-documents-windows-and-views.md)中的 "管理 MFC 模块的状态数据" 和[技术说明 58](../tn058-mfc-module-state-implementation.md)。

### <a name="requirements"></a>要求

**标头：** afxstat_。h

## <a name="afxinitextensionmodule"></a>AfxInitExtensionModule

在 MFC 扩展 DLL 的 `DllMain` 中调用此函数以初始化 DLL。

### <a name="syntax"></a>语法

```
BOOL AFXAPI AfxInitExtensionModule( AFX_EXTENSION_MODULE& state,  HMODULE hModule );
```

### <a name="parameters"></a>parameters

State<br/>
对[AFX_EXTENSION_MODULE 结构](afx-extension-module-structure.md)结构的引用，该结构将包含初始化后的 MFC 扩展 DLL 模块的状态。 该状态包含一个运行时类对象的副本，这些对象已由 MFC 扩展 DLL 初始化，作为在输入 `DllMain` 之前执行的常规静态对象构造的一部分。

*hModule*<br/>
MFC 扩展 DLL 模块的句柄。

### <a name="return-value"></a>返回值

如果 MFC 扩展 DLL 已成功初始化，则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

例如：

```cpp
static AFX_EXTENSION_MODULE NVC_MFC_DLLDLL = { NULL, NULL };
extern "C" int APIENTRY
DllMain(HINSTANCE hInstance, DWORD dwReason, LPVOID lpReserved)
{
    // Remove this if you use lpReserved
    UNREFERENCED_PARAMETER(lpReserved);

    if (dwReason == DLL_PROCESS_ATTACH)
    {
        TRACE0("NVC_MFC_DLL.DLL Initializing!\n");

        // MFC extension DLL one-time initialization
        if (!AfxInitExtensionModule(NVC_MFC_DLLDLL, hInstance))
            return 0;
...
```

`AfxInitExtensionModule` 生成 DLL HMODULE 的副本，并捕获 DLL 的运行时类（`CRuntimeClass` 结构）及其对象工厂（`COleObjectFactory` 对象），以便以后在创建 `CDynLinkLibrary` 对象时使用。
MFC 扩展 Dll 需要在其 `DllMain` 函数中执行两项操作：

- 调用[AfxInitExtensionModule](#afxinitextensionmodule)并检查返回值。

- 如果 DLL 将导出[CRuntimeClass 结构](cruntimeclass-structure.md)对象或有其自己的自定义资源，请创建 `CDynLinkLibrary` 对象。

当每个进程从 MFC 扩展 DLL 分离时（发生在进程退出时，或者当 DLL 作为 `AfxFreeLibrary` 调用的结果而卸载时），可以调用 `AfxTermExtensionModule` 来清理 MFC 扩展 DLL。

### <a name="requirements"></a>要求

**标头：** afxdll_。h

## <a name="afxsetambientactctx"></a>AfxSetAmbientActCtx

使用以下函数可设置每个模块的状态标志，该标志影响 MFC 的 WinSxS 行为。

### <a name="syntax"></a>语法

```
void AFXAPI AfxSetAmbientActCtx(BOOL bSet);
```

### <a name="parameters"></a>parameters

*bSet*<br/>
模块状态标志的新值。

### <a name="remarks"></a>备注

如果设置了标志（这是默认设置），并且一个线程进入 MFC 模块（请参阅[AFX_MANAGE_STATE](#afx_manage_state)），则激活模块的上下文。
如果未设置该标志，则线程进入时不会激活模块的上下文。
模块的上下文从其清单确定，通常会嵌入模块资源。

### <a name="example"></a>示例

```cpp
BOOL CMFCListViewApp::InitInstance()
{
   AfxSetAmbientActCtx(FALSE);
   // Remainder of function definition omitted.
}
```

### <a name="requirements"></a>要求

**标头：** afxcomctl32。h

## <a name="afxtermextensionmodule"></a>AfxTermExtensionModule

调用此函数可在每个进程从 DLL 分离时（发生在进程退出时，或当 DLL 作为 `AfxFreeLibrary` 调用的结果而卸载时），允许 MFC 清除 MFC 扩展 DLL。

### <a name="syntax"></a>语法

```
void AFXAPI AfxTermExtensionModule(  AFX_EXTENSION_MODULE& state,  BOOL bAll  = FALSE );
```

### <a name="parameters"></a>parameters

State<br/>
对包含 MFC 扩展 DLL 模块状态的[AFX_EXTENSION_MODULE](afx-extension-module-structure.md)结构的引用。

*滚*<br/>
如果为 TRUE，则清理所有 MFC 扩展 DLL 模块。 否则，仅清理当前 DLL 模块。

### <a name="remarks"></a>备注

`AfxTermExtensionModule` 将删除附加到该模块的任何本地存储，并从消息映射缓存中删除任何条目。 例如：

```cpp
static AFX_EXTENSION_MODULE NVC_MFC_DLLDLL = { NULL, NULL };
extern "C" int APIENTRY
DllMain(HINSTANCE hInstance, DWORD dwReason, LPVOID lpReserved)
{
    // Remove this if you use lpReserved
    UNREFERENCED_PARAMETER(lpReserved);

    if (dwReason == DLL_PROCESS_ATTACH)
    {
        TRACE0("NVC_MFC_DLL.DLL Initializing!\n");

        // MFC extension DLL one-time initialization
        if (!AfxInitExtensionModule(NVC_MFC_DLLDLL, hInstance))
            return 0;

        new CMyDynLinkLibrary(NVC_MFC_DLLDLL);

    }
    else if (dwReason == DLL_PROCESS_DETACH)
    {
        TRACE0("NVC_MFC_DLL.DLL Terminating!\n");

        // Terminate the library before destructors are called
        AfxTermExtensionModule(NVC_MFC_DLLDLL);
    }
    return 1;   // ok
}
```

如果你的应用程序动态加载和释放 MFC 扩展 Dll，请确保调用 `AfxTermExtensionModule`。 由于大多数 MFC 扩展 Dll 都未动态加载（通常是通过它们的导入库进行链接），因此通常不需要调用 `AfxTermExtensionModule`。

MFC 扩展 Dll 需要在其 `DllMain`中调用[AfxInitExtensionModule](#afxinitextensionmodule) 。 如果 DLL 将导出[CRuntimeClass](cruntimeclass-structure.md)对象或有自己的自定义资源，还需要在 `DllMain`中创建 `CDynLinkLibrary` 对象。

### <a name="requirements"></a>要求

**标头：** afxdll_。h

## <a name="see-also"></a>另请参阅

[宏和全局](mfc-macros-and-globals.md)<br/>
[AfxMessageBox](cstring-formatting-and-message-box-display.md#afxmessagebox)<br/>
[管理 MFC 模块的状态数据](../managing-the-state-data-of-mfc-modules.md)<br/>
