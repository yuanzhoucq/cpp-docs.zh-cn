---
title: 用于管理 DLL 的宏和函数
ms.date: 03/27/2019
helpviewer_keywords:
- module macros in MFC
ms.assetid: 303f4161-cb5e-4099-81ad-acdb11aa60fb
ms.openlocfilehash: 42a08ff2e806acae6713c9df3fe170f7e89f05af
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81751600"
---
# <a name="macros-and-functions-for-managing-dlls"></a>用于管理 DLL 的宏和函数

|||
|-|-|
|[AFX_EXT_CLASS](#afx_ext_class)||导出类。|
|[AFX_MANAGE_STATE](#afx_manage_state)|保护 DLL 中的导出函数。|
|[AfxOleInitModule](#afxoleinitmodule)|从动态链接到 MFC 的常规 MFC DLL 提供 OLE 支持。|
|[AfxNetInitModule](#afxnetinitmodule)|提供与 MFC 动态链接的常规 MFC DLL 的 MFC 插槽支持。|
|[AfxGetAmbientActCtx](#afxgetambientactctx)|获取每个模块状态标志的当前状态。|
|[AfxGetStaticModuleState](#afxgetstaticmodulestate)|在初始化和/或清理后还原以前的模块状态之前设置模块状态。|
|[AfxInitExtensionModule](#afxinitextensionmodule)|初始化 DLL。|
|[AfxSetAmbientActCtx](#afxsetambientactctx)|设置每个模块的状态标志，这会影响 MFC 的 WinSxS 行为。|
|[AfxTermExtensionModule](#afxtermextensionmodule)|允许 MFC 在每个进程从 DLL 分离时清理 MFC 扩展 DLL。|

## <a name="afx_ext_class"></a><a name="afx_ext_class"></a>AFX_EXT_CLASS

[MFC 扩展 DLL](../../build/extension-dlls.md)使用宏AFX_EXT_CLASS导出类;链接到 MFC 扩展 DLL 的可执行文件使用宏导入类。

### <a name="remarks"></a>备注

使用AFX_EXT_CLASS宏时，用于构建 MFC 扩展名 DLL 的相同标头文件可用于链接到 DLL 的可执行文件。

在 DLL 的标头文件中，将AFX_EXT_CLASS关键字添加到类的声明中，如下所示：

```cpp
class AFX_EXT_CLASS CMyClass : public CDocument
{
// <body of class>
};
```

有关详细信息，请参阅使用[AFX_EXT_CLASS 导出和导入](../../build/exporting-and-importing-using-afx-ext-class.md)。

### <a name="requirements"></a>要求

**标题：** afxv_dll.h

## <a name="afx_manage_state"></a><a name="afx_manage_state"></a>AFX_MANAGE_STATE

调用此宏以保护 DLL 中的导出函数。

### <a name="syntax"></a>语法

```
AFX_MANAGE_STATE(AFX_MODULE_STATE* pModuleState )
```

### <a name="parameters"></a>参数

*pModuleState*<br/>
指向结构的`AFX_MODULE_STATE`指针。

### <a name="remarks"></a>备注

调用此宏时 *，pModuleState*是直接包含作用域其余部分的有效模块状态。 离开作用域后，将自动还原以前的有效模块状态。
结构`AFX_MODULE_STATE`包含模块的全局数据，即推送或弹出的模块状态部分。

默认情况下，MFC 使用主应用程序的资源句柄来加载资源模板。 如果在 DLL 中具有导出的函数（例如在 DLL 中启动对话框的函数），则此模板实际上存储在 DLL 模块中。 您需要切换模块状态才能使用正确的句柄。 可以通过将以下代码添加到函数的开头来执行此操作：

```cpp
AFX_MANAGE_STATE(AfxGetStaticModuleState( ));
```

这将将当前模块状态与从[AfxGetStaticModuleState](#afxgetstaticmodulestate)返回的状态交换，直到当前作用域结束。

有关模块状态和 MFC 的详细信息，请参阅[创建新文档、Windows 和视图](../creating-new-documents-windows-and-views.md)[和技术说明 58](../tn058-mfc-module-state-implementation.md)中的"管理 MFC 模块的状态数据"。

> [!NOTE]
> 当 MFC 为程序集创建激活上下文时，它使用[AfxWinInit](application-information-and-management.md#afxwininit)创建上下文`AFX_MANAGE_STATE`并激活和停用它。 另请注意，`AFX_MANAGE_STATE`为静态 MFC 库以及 MFC DLL 启用，以便允许 MFC 代码在用户 DLL 选择的正确激活上下文中执行。 有关详细信息，请参阅[MFC 模块状态中对激活上下文的支持](../support-for-activation-contexts-in-the-mfc-module-state.md)。

### <a name="requirements"></a>要求

**标题：** afxstat_.h

## <a name="a-nameafxoleinitmodule-afxoleinitmodule"></a><a name="afxoleinitmodule"><a/>阿FXOleinit模块

对于动态链接到 MFC 的常规 MFC DLL 的 OLE 支持，请在常规 MFC DLL`CWinApp::InitInstance`函数中调用此功能以初始化 MFC OLE DLL。

### <a name="syntax"></a>语法

```cpp
void AFXAPI AfxOleInitModule( );
```

### <a name="remarks"></a>备注

MFC OLE DLL 是 MFC 扩展 DLL;为了使 MFC 扩展 DLL 连接到`CDynLinkLibrary`链中，它必须在将使用它的每个模块`CDynLinkLibrary`的上下文中创建一个对象。 `AfxOleInitModule`在`CDynLinkLibrary`常规 MFC DLL 的上下文中创建对象，以便将其连接到常规 MFC DLL`CDynLinkLibrary`的对象链中。

如果要构建 OLE 控件并且正在`COleControlModule`使用 ，则不应调用`AfxOleInitModule`，因为`InitInstance``COleControlModule`调用`AfxOleInitModule`的成员函数。

### <a name="requirements"></a>要求

**标题** \<： afxdll_.h>

## <a name="afxnetinitmodule"></a><a name="afxnetinitmodule"></a>AfxNetInit 模块

对于动态链接到 MFC 的常规 MFC DLL 的 MFC 插槽支持，在常规 MFC DLL 函数中添加对此函数`CWinApp::InitInstance`的调用，以初始化 MFC 插槽 DLL。

### <a name="syntax"></a>语法

```cpp
void AFXAPI AfxNetInitModule( );
```

### <a name="remarks"></a>备注

MFC 插槽 DLL 是 MFC 扩展 DLL;为了使 MFC 扩展 DLL 连接到`CDynLinkLibrary`链中，它必须在将使用它的每个模块`CDynLinkLibrary`的上下文中创建一个对象。 `AfxNetInitModule`在`CDynLinkLibrary`常规 MFC DLL 的上下文中创建对象，以便将其连接到常规 MFC DLL`CDynLinkLibrary`的对象链中。

### <a name="requirements"></a>要求

**标题：** \<afxdll_.h>

## <a name="afxgetambientactctx"></a><a name="afxgetambientactctx"></a>AfxGet环境ActCtx

使用此函数获取每个模块状态标志的当前状态，这会影响 MFC 的 WinSxS 行为。

### <a name="syntax"></a>语法

```
BOOL AFXAPI AfxGetAmbientActCtx();
```

### <a name="return-value"></a>返回值

模块状态标志当前值。

### <a name="remarks"></a>备注

当标志被设置（这是默认值）和线程进入 MFC 模块（请参阅[AFX_MANAGE_STATE），](#afx_manage_state)模块的上下文被激活。

如果未设置该标志，则线程进入时不会激活模块的上下文。

模块的上下文从其清单确定，通常会嵌入模块资源。

### <a name="requirements"></a>要求

**标题：** afxcomctl32.h

## <a name="afxgetstaticmodulestate"></a><a name="afxgetstaticmodulestate"></a>AfxGet静态模块状态

调用此函数以在初始化之前设置模块状态和/或在清理后还原以前的模块状态。

### <a name="syntax"></a>语法

```
AFX_MODULE_STATE* AFXAPI AfxGetStaticModuleState( );
```

### <a name="return-value"></a>返回值

指向结构的`AFX_MODULE_STATE`指针。

### <a name="remarks"></a>备注

结构`AFX_MODULE_STATE`包含模块的全局数据，即推送或弹出的模块状态部分。

默认情况下，MFC 使用主应用程序的资源句柄来加载资源模板。 如果在 DLL 中具有导出的函数（例如在 DLL 中启动对话框的函数），则此模板实际上存储在 DLL 模块中。 您需要切换模块状态才能使用正确的句柄。 可以通过将以下代码添加到函数的开头来执行此操作：

```cpp
AFX_MANAGE_STATE(AfxGetStaticModuleState( ));
```

这将交换当前模块状态，从当前作用域结束`AfxGetStaticModuleState`为止返回的状态。

有关模块状态和 MFC 的详细信息，请参阅[创建新文档、Windows 和视图](../creating-new-documents-windows-and-views.md)[和技术说明 58](../tn058-mfc-module-state-implementation.md)中的"管理 MFC 模块的状态数据"。

### <a name="requirements"></a>要求

**标题：** afxstat_.h

## <a name="afxinitextensionmodule"></a>AfxInitExtensionModule

在 MFC 扩展 DLL 中调用`DllMain`此函数以初始化 DLL。

### <a name="syntax"></a>语法

```
BOOL AFXAPI AfxInitExtensionModule( AFX_EXTENSION_MODULE& state,  HMODULE hModule );
```

### <a name="parameters"></a>参数

State <br/>
对[AFX_EXTENSION_MODULE结构结构](afx-extension-module-structure.md)的引用，该结构将在初始化后包含 MFC 扩展 DLL 模块的状态。 状态包括 MFC 扩展 DLL 已初始化的运行时类对象的副本，作为输入之前`DllMain`执行的正常静态对象构造的一部分。

*hModule*<br/>
MFC 扩展 DLL 模块的句柄。

### <a name="return-value"></a>返回值

如果 MFC 扩展 DLL 已成功初始化，则为 TRUE;否则，FALSE。

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

`AfxInitExtensionModule`复制 DLL 的 HMODULE 并捕获 DLL 的运行时类（`CRuntimeClass`结构）及其对象工厂（`COleObjectFactory`对象），供以后创建`CDynLinkLibrary`对象时使用。
MFC 扩展 DLL 需要在其`DllMain`功能中执行两项操作：

- 调用[AfxInit 扩展模块](#afxinitextensionmodule)并检查返回值。

- 如果`CDynLinkLibrary`DLL 将导出[CRuntimeClass 结构](cruntimeclass-structure.md)对象或具有其自己的自定义资源，则创建对象。

当每个进程`AfxTermExtensionModule`从 MFC 分机 DLL 分离时（当进程退出时，或者由于`AfxFreeLibrary`调用而卸载 DLL 时），可以调用以清理 MFC 分机 DLL。

### <a name="requirements"></a>要求

**标题：** afxdll_.h

## <a name="afxsetambientactctx"></a><a name="afxsetambientactctx"></a>AfxSet环境ActCtx

使用以下函数可设置每个模块的状态标志，该标志影响 MFC 的 WinSxS 行为。

### <a name="syntax"></a>语法

```cpp
void AFXAPI AfxSetAmbientActCtx(BOOL bSet);
```

### <a name="parameters"></a>参数

*bSet*<br/>
模块状态标志的新值。

### <a name="remarks"></a>备注

当标志被设置（这是默认值）和线程进入 MFC 模块（请参阅[AFX_MANAGE_STATE），](#afx_manage_state)模块的上下文被激活。
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

**标题：** afxcomctl32.h

## <a name="afxtermextensionmodule"></a><a name="afxtermextensionmodule"></a>AfxTerm扩展模块

调用此函数，允许 MFC 在每个进程从 DLL 分离时（当进程退出或由于`AfxFreeLibrary`调用而卸载 DLL 时）清理 MFC 分机 DLL。

### <a name="syntax"></a>语法

```cpp
void AFXAPI AfxTermExtensionModule(  AFX_EXTENSION_MODULE& state,  BOOL bAll  = FALSE );
```

### <a name="parameters"></a>参数

State <br/>
对包含 MFC 扩展 DLL 模块状态[AFX_EXTENSION_MODULE结构的](afx-extension-module-structure.md)引用。

*球*<br/>
如果为 TRUE，请清理所有 MFC 扩展 DLL 模块。 否则，请仅清理当前 DLL 模块。

### <a name="remarks"></a>备注

`AfxTermExtensionModule`将删除附加到模块的任何本地存储，并从消息映射缓存中删除任何条目。 例如：

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

如果应用程序动态加载并释放 MFC 扩展 DLL，请务必调用`AfxTermExtensionModule`。 由于大多数 MFC 扩展 DLL 不是动态加载的（通常，它们通过其导入库链接），因此通常`AfxTermExtensionModule`不需要调用 。

MFC 扩展 DLL 需要在其`DllMain`中调用[AfxInit 扩展模块](#afxinitextensionmodule)。 如果 DLL 将导出[CRuntimeClass](cruntimeclass-structure.md)对象或有自己的自定义资源，则还需要在 中`CDynLinkLibrary``DllMain`创建一个对象。

### <a name="requirements"></a>要求

**标题：** afxdll_.h

## <a name="see-also"></a>请参阅

[MFC 宏和全局函数](mfc-macros-and-globals.md)<br/>
[AfxMessageBox](cstring-formatting-and-message-box-display.md#afxmessagebox)<br/>
[管理 MFC 模块的状态数据](../managing-the-state-data-of-mfc-modules.md)<br/>
