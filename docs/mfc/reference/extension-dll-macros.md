---
title: 宏和功能，用于管理 Dll |Microsoft 文档
ms.custom: ''
ms.date: 04/03/2017
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- module macros in MFC
ms.assetid: 303f4161-cb5e-4099-81ad-acdb11aa60fb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e5e79556bf6e3ae92f7a8d4975dbd30f199e2ca8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33376471"
---
# <a name="macros-and-functions-for-managing-dlls"></a>宏和用于管理 Dll 函数

|||
|-|-|
|[AFX_EXT_CLASS](#afx_ext_class)]|导出类。|
|[AFX_MANAGE_STATE](#afx_manage_state)|保护在 DLL 中导出的函数。|
|[AfxOleInitModule](#afxoleinitmodule)|提供 OLE 支持从动态链接到 MFC 常规 MFC DLL。|
|[AfxNetInitModule](#afxnetinitmodule)|提供 MFC 套接字支持从动态链接到 MFC 常规 MFC DLL。|
|[AfxGetAmbientActCtx](#afxgetambientactctx)|获取每个模块状态标志的当前状态。|
|[AfxGetStaticModuleState](#afxgetstaticmodulestate)|设置在初始化之前和/或清理后还原以前的模块状态的模块状态。|
|[AfxInitExtensionModule]()#afxinitextensionmodule|初始化 DLL。|
|[AfxSetAmbientActCtx](#afxsetambientactctx)|设置每个模块状态标志，这会影响 MFC 的 WinSxS 行为。|
|[AfxTermExtensionModule]()#afxtermextensionmodule)|允许 MFC 清理 MFC 扩展 DLL 时从 DLL 中每个进程分离。|


## <a name="afx_ext_class"></a>  AFX_EXT_CLASS
[MFC 扩展 Dll](../../build/extension-dlls.md)使用宏**AFX_EXT_CLASS**导出类; 链接到 MFC 扩展 DLL 的可执行文件使用宏来导入类。  
   
### <a name="remarks"></a>备注  
 与**AFX_EXT_CLASS**宏，用于生成 MFC 扩展 DLL 的文件可以用于链接到 DLL 的可执行文件的同一个标头。  
  
 在为 DLL 标头文件中，添加**AFX_EXT_CLASS**到你的类，如下所示的声明的关键字：  
  
```cpp
class AFX_EXT_CLASS CMyClass : public CDocument
{
// <body of class>
};
``` 
  
 有关详细信息，请参阅[导出和导入使用 AFX_EXT_CLASS](../../build/exporting-and-importing-using-afx-ext-class.md)。  
   
### <a name="requirements"></a>要求  
 标头： **afxv_** dll.h  
   
## <a name="afx_manage_state"></a>  AFX_MANAGE_STATE
调用此宏，以免在 DLL 中导出的函数。  
   
### <a name="syntax"></a>语法    
```
AFX_MANAGE_STATE(AFX_MODULE_STATE* pModuleState )  
```
### <a name="parameters"></a>参数  
 `pModuleState`  
 指向的指针`AFX_MODULE_STATE`结构。  
   
### <a name="remarks"></a>备注  
 此宏调用时，`pModuleState`最接近的其余部分的有效模块状态包含作用域。 一旦离开范围，将自动还原以前的有效模块状态。    
 `AFX_MODULE_STATE`结构包含模块，即是推送或弹出的模块状态的部分的全局数据。    
 默认情况下，MFC 使用主应用程序的资源句柄来加载资源模板。 如果你有导出的函数的 DLL，例如启动 DLL 中的对话框中此模板实际存储在 DLL 模块中。 你需要切换为正确的句柄，要使用的模块状态。 可以通过将下面的代码添加到函数的开头来执行此操作：    
```cpp
AFX_MANAGE_STATE(AfxGetStaticModuleState( ));

```
 此交换与从返回的状态将当前模块状态[AfxGetStaticModuleState](#afxgetstaticmodulestate)直至当前范围的末尾。    
 模块状态和 MFC 的详细信息，请参阅"管理数据的 MFC 模块状态"中[创建新文档、 窗口和视图](../creating-new-documents-windows-and-views.md)和[技术说明 58](../tn058-mfc-module-state-implementation.md)。    
> [!NOTE]
>  当 MFC 将为程序集创建激活上下文时，它会使用[AfxWinInit](#afxwininit)若要创建的上下文和`AFX_MANAGE_STATE`激活和停用它。 另请注意，`AFX_MANAGE_STATE`为静态 MFC 库以及 MFC Dll 启用才能使 MFC 代码在用户 DLL 选择的正确激活上下文中执行。 有关详细信息，请参阅[MFC 模块状态中的激活上下文的支持](../support-for-activation-contexts-in-the-mfc-module-state.md)。     
### <a name="requirements"></a>要求  
 **标头：** afxstat_.h  
   
### <a name="see-also"></a>请参阅  
 [AfxGetStaticModuleState](#afxgetstaticmodulestate)

## <a name="a-nameafxoleinitmodulea-afxoleinitmodule"></a><a name="afxoleinitmodule"><a/> AfxOleInitModule
OLE 从动态链接到 MFC 常规 MFC DLL 的支持，为常规 MFC DLL 中调用此函数`CWinApp::InitInstance`函数可以初始化 MFC OLE DLL。  
   
### <a name="syntax"></a>语法    
```
void AFXAPI AfxOleInitModule( );  
```  
   
### <a name="remarks"></a>备注  
 MFC OLE DLL 是 MFC 扩展 DLL;使 MFC 扩展 DLL，若要连接到**CDynLinkLibrary**链，它必须创建**CDynLinkLibrary**将使用它的每个模块的上下文中的对象。 `AfxOleInitModule` 创建**CDynLinkLibrary**对象常规 MFC DLL 的上下文中，以便让它连接到**CDynLinkLibrary**对象常规 MFC dll 的链。  
  
 如果你要生成 OLE 控件并将`COleControlModule`，不应调用**AfxOleInitModule**因为`InitInstance`成员函数，`COleControlModule`调用`AfxOleInitModule`。  
   
### <a name="requirements"></a>要求  
 **标头**: < afxdll_.h >  
   
### <a name="see-also"></a>请参阅  
 [宏和全局函数](mfc-macros-and-globals.md)   
 [AfxMessageBox](cstring-formatting-and-message-box-display.md#afxmessagebox)

## <a name="afxnetinitmodule"></a>  AfxNetInitModule
MFC 套接字支持从动态链接到 MFC 常规 MFC DLL 的支持，在常规 MFC DLL 中添加对此函数的调用**CWinApp::InitInstance**函数可以初始化 MFC 套接字 DLL。  
   
### <a name="syntax"></a>语法    
```
void AFXAPI AfxNetInitModule( );  
```  
   
### <a name="remarks"></a>备注  
 MFC 套接字 DLL 是 MFC 扩展 DLL;使 MFC 扩展 DLL，若要连接到**CDynLinkLibrary**链，它必须创建**CDynLinkLibrary**将使用它的每个模块的上下文中的对象。 `AfxNetInitModule` 创建**CDynLinkLibrary**对象常规 MFC DLL 的上下文中，以便让它连接到**CDynLinkLibrary**对象常规 MFC dll 的链。  
   
### <a name="requirements"></a>要求  
 **标头：** < afxdll_.h >  
   
### <a name="see-also"></a>请参阅  
 [宏和全局函数](mfc-macros-and-globals.md)   
 [AfxMessageBox](cstring-formatting-and-message-box-display.md#afxmessagebox)

## <a name="afxgetambientactctx"></a> AfxGetAmbientActCtx
此函数用于获取每个模块状态标志影响 MFC 的 WinSxS 行为的当前状态。  
   
### <a name="syntax"></a>语法    
```  
BOOL AFXAPI AfxGetAmbientActCtx();   
```  
   
### <a name="return-value"></a>返回值  
 模块状态标志当前值。  
   
### <a name="remarks"></a>备注  
 已设置的标志 （这是默认值） 并且线程进入 MFC 模块时 (请参阅[AFX_MANAGE_STATE](#afx_manage_state))，激活模块的上下文。  
  
 如果未设置该标志，则线程进入时不会激活模块的上下文。  
  
 模块的上下文从其清单确定，通常会嵌入模块资源。  
   
### <a name="requirements"></a>要求  
 **标头：** afxcomctl32.h  
   
### <a name="see-also"></a>请参阅  
 [宏和全局函数](mfc-macros-and-globals.md)   
 [AFX_MANAGE_STATE](#afx_manage_state)   
 [管理 MFC 模块的状态数据](../managing-the-state-data-of-mfc-modules.md)   
 [AfxSetAmbientActCtx](#setambientactctx)
 
## <a name="afxgetstaticmodulestate"></a> AfxGetStaticModuleState
调用此函数可设置在初始化之前的模块状态和/或清理后还原以前的模块状态。  
   
### <a name="syntax"></a>语法    
```
AFX_MODULE_STATE* AFXAPI AfxGetStaticModuleState( );  
```  
   
### <a name="return-value"></a>返回值  
 指向的指针`AFX_MODULE_STATE`结构。  
   
### <a name="remarks"></a>备注  
 `AFX_MODULE_STATE`结构包含模块，即是推送或弹出的模块状态的部分的全局数据。  
  
 默认情况下，MFC 使用主应用程序的资源句柄来加载资源模板。 如果你有导出的函数的 DLL，例如启动 DLL 中的对话框中此模板实际存储在 DLL 模块中。 你需要切换为正确的句柄，要使用的模块状态。 可以通过将下面的代码添加到函数的开头来执行此操作：  
  
```cpp
AFX_MANAGE_STATE(AfxGetStaticModuleState( ));

```
  
 此交换与从返回的状态将当前模块状态`AfxGetStaticModuleState`直至当前范围的末尾。  
  
 模块状态和 MFC 的详细信息，请参阅"管理数据的 MFC 模块状态"中[创建新文档、 窗口和视图](../creating-new-documents-windows-and-views.md)和[技术说明 58](../tn058-mfc-module-state-implementation.md)。  
   
### <a name="requirements"></a>要求  
 **标头：** afxstat_.h  
   

## <a name="afxinitextensionmodule"></a> AfxInitExtensionModule
调用此函数在 MFC 扩展 DLL 的`DllMain`初始化该 DLL。  
   
### <a name="syntax"></a>语法    
```
BOOL AFXAPI AfxInitExtensionModule( AFX_EXTENSION_MODULE& state,  HMODULE hModule );  
```
### <a name="parameters"></a>参数  
 `state`  
 对引用[AFX_EXTENSION_MODULE 结构](afx-extension-module-structure.md)结构，它将在初始化后包含 MFC 扩展 DLL 模块的状态。 状态包括已通过 MFC 扩展 DLL 初始化为正常的静态对象构造之前执行的一部分运行时类对象的副本`DllMain`输入。  
  
 `hModule`  
 MFC 扩展 DLL 模块的句柄。  
   
### <a name="return-value"></a>返回值  
 **TRUE** MFC 扩展 DLL 是否已成功初始化; 否则为**FALSE**。  
   
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

```
  
 `AfxInitExtensionModule` 生成的 DLL 的副本**HMODULE**和捕获 DLL 的运行时类 (`CRuntimeClass`结构) 以及其对象工厂 (`COleObjectFactory`对象) 用于更高版本在**CDynLinkLibrary**创建对象。    
 MFC 扩展 Dll 需要执行两项操作在其`DllMain`函数：    
-   调用[AfxInitExtensionModule](#_mfc_afxinitextensionmodule)并检查返回的值。   
-   创建**CDynLinkLibrary**对象如果 DLL 将导出[CRuntimeClass 结构](cruntimeclass-structure.md)对象，或在具有其自己的自定义资源。    
 你可以调用`AfxTermExtensionModule`清理 MFC 扩展 DLL，每个进程从 MFC 扩展 DLL 中分离时 (这发生在进程退出，或为卸载 DLL`AfxFreeLibrary`调用)。     

### <a name="requirements"></a>要求  
 **标头：** afxdll_.h     

### <a name="see-also"></a>请参阅  
 [宏和全局函数](mfc-macros-and-globals.md)   
 [AfxTermExtensionModule](#afxtermextensionmodule)

 ## <a name="afxsetambientactctx"></a>  AfxSetAmbientActCtx
使用以下函数可设置每个模块的状态标志，该标志影响 MFC 的 WinSxS 行为。  
   
### <a name="syntax"></a>语法  
  ```
   void AFXAPI AfxSetAmbientActCtx( BOOL bSet  
);  
```
### <a name="parameters"></a>参数  
 `bSet`  
 模块状态标志的新值。  
   
### <a name="remarks"></a>备注  
 已设置的标志 （这是默认值） 并且线程进入 MFC 模块时 (请参阅[AFX_MANAGE_STATE](#afx_manage_state))，激活模块的上下文。    
 如果未设置该标志，则线程进入时不会激活模块的上下文。    
 模块的上下文从其清单确定，通常会嵌入模块资源。  
   
### <a name="example"></a>示例  
 ```cpp
BOOL CMFCListViewApp::InitInstance()
{
   AfxSetAmbientActCtx(FALSE);
   // Remainder of function definition omitted.
```
   
### <a name="requirements"></a>要求  
 **标头：** afxcomctl32.h  
   
### <a name="see-also"></a>请参阅  
 [宏和全局函数](mfc-macros-and-globals.md)   
 [AfxGetAmbientActCtx](#afxgetambientactctx)   
 [AFX_MANAGE_STATE](#afx_manage_state)   
 [管理 MFC 模块的状态数据](../managing-the-state-data-of-mfc-modules.md) 

## <a name="afxtermextensionmodule"></a>  AfxTermExtensionModule

调用此函数，以允许在 MFC 清理 MFC 扩展 DLL 时每个进程从 DLL 中分离 (这发生在进程退出，或为卸载 DLL`AfxFreeLibrary`调用)。  
   
### <a name="syntax"></a>语法  
  ```
void AFXAPI AfxTermExtensionModule(  AFX_EXTENSION_MODULE& state,  BOOL bAll  = FALSE );  
```
### <a name="parameters"></a>参数  
 `state`  
 对引用[AFX_EXTENSION_MODULE](afx-extension-module-structure.md)结构，其中包含 MFC 扩展 DLL 模块的状态。  
  
 *球*  
 如果**TRUE**、 清除所有 MFC 扩展 DLL 模块。 否则为清除仅当前 DLL 模块。  
   
### <a name="remarks"></a>备注  
 `AfxTermExtensionModule` 将删除任何连接到该模块的本地存储和从消息映射缓存中删除任何条目。 例如：  
  
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
  
 如果你的应用程序加载，并动态释放 MFC 扩展 Dll，一定要调用`AfxTermExtensionModule`。 由于不会动态加载 Dll 的大多数 MFC 扩展 （通常情况下，它们在连接通过其导入库），调用`AfxTermExtensionModule`通常是不必要。  
  
 MFC 扩展 Dll 需要调用[AfxInitExtensionModule](#afxinitextensionmodule)中其`DllMain`。 如果 DLL 将导出[CRuntimeClass](cruntimeclass-structure.md)对象，或在具有其自己的自定义资源，还需要创建**CDynLinkLibrary**对象在`DllMain`。  
   
### <a name="requirements"></a>要求  
 **标头：** afxdll_.h  
   
### <a name="see-also"></a>请参阅  
 [宏和全局函数](mfc-macros-and-globals.md)   
 [AfxInitExtensionModule](#afxinitextensionmodule)
 




