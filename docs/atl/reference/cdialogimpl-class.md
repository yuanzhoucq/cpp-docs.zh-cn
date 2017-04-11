---
title: "CDialogImpl 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDialogImpl
- ATLWIN/ATL::CDialogImpl
- ATLWIN/ATL::Create
- ATLWIN/ATL::DestroyWindow
- ATLWIN/ATL::DoModal
- ATLWIN/ATL::EndDialog
- ATLWIN/ATL::GetDialogProc
- ATLWIN/ATL::MapDialogRect
- ATLWIN/ATL::OnFinalMessage
- ATLWIN/ATL::DialogProc
- ATLWIN/ATL::StartDialogProc
dev_langs:
- C++
helpviewer_keywords:
- dialog boxes, ATL
- CDialogImpl class
ms.assetid: d430bc7b-8a28-4ad3-9507-277bdd2c2c2e
caps.latest.revision: 25
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: d2d39abf526a58b8442107b5ee816f316ae841f5
ms.openlocfilehash: 76a95ed5c32b2125112b64ef4368e4a82f0acec0
ms.lasthandoff: 03/31/2017

---
# <a name="cdialogimpl-class"></a>CDialogImpl 类
此类提供用于创建模式或无模式对话框中的方法。  
  
> [!IMPORTANT]
>  此类及其成员无法在 Windows 运行时中执行的应用中使用。  
  
## <a name="syntax"></a>语法  
  
```  
 
template <class T,  
    class TBase = CWindow>  
    class ATL_NO_VTABLE CDialogImpl : public CDialogImplBaseT<TBase>  
 
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 你的类，派生自`CDialogImpl`。  
  
 *TBase*  
 在新类的基类。 默认基类是[CWindow](../../atl/reference/cwindow-class.md)。  
  
## <a name="members"></a>成员  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[创建](#create)|创建无模式对话框。|  
|[DestroyWindow](#destroywindow)|销毁无模式对话框。|  
|[DoModal](#domodal)|创建模式对话框。|  
|[EndDialog](#enddialog)|销毁模式对话框。|  
  
### <a name="cdialogimplbaset-methods"></a>CDialogImplBaseT 方法  
  
|||  
|-|-|  
|[GetDialogProc](#getdialogproc)|返回当前对话框过程。|  
|[MapDialogRect](#mapdialogrect)|将指定的矩形的对话框单位映射到屏幕单位 （像素）。|  
|[OnFinalMessage](#onfinalmessage)|在通常接收最后一条消息之后, 调用`WM_NCDESTROY`。|  
  
### <a name="static-functions"></a>静态函数  
  
|||  
|-|-|  
|[DialogProc](#dialogproc)|处理发送到对话框中的消息。|  
|[StartDialogProc](#startdialogproc)|收到第一条消息来处理发送到对话框中的消息时调用。|  
  
## <a name="remarks"></a>备注  
 与`CDialogImpl`可以创建一个模式或无模式对话框。 `CDialogImpl`提供对话框过程，使用默认消息映射来将消息定向到相应的处理程序。  
  
 基类析构函数**~ CWindowImplRoot**可确保窗口已销毁对象之前中消除。  
  
 `CDialogImpl`派生自**CDialogImplBaseT**，它又派生自**CWindowImplRoot**。  
  
> [!NOTE]
>  你的类必须定义**IDD**成员，用于指定对话框模板资源 id。 例如，ATL 项目向导自动将以下行添加到你的类︰  
  
 [!code-cpp[NVC_ATL_Windowing # 41](../../atl/codesnippet/cpp/cdialogimpl-class_1.h)]  
  
 其中`MyDlg`是**短名称**在向导中输入**名称**页。  
  
|有关以下内容的详细信息|请参阅|  
|--------------------------------|---------|  
|创建控件|[ATL 教程](../../atl/active-template-library-atl-tutorial.md)|  
|使用 ATL 中的对话框|[ATL 窗口类](../../atl/atl-window-classes.md)|  
|ATL 项目向导|[创建 ATL 项目](../../atl/reference/creating-an-atl-project.md)|  
|对话框|[对话框](http://msdn.microsoft.com/library/windows/desktop/ms632588)和后续主题中的[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]|  
  
## <a name="requirements"></a>要求  
 **标头︰** atlwin.h  
  
##  <a name="create"></a>CDialogImpl::Create  
 创建无模式对话框。  
  
```  
HWND Create(
    HWND hWndParent,  
    LPARAM dwInitParam = NULL );  

HWND Create(
    HWND hWndParent,  
    RECT&, 
    LPARAM dwInitParam = NULL); 
```  
  
### <a name="parameters"></a>参数  
 `hWndParent`  
 [in]向所有者窗口句柄。  
  
 **RECT &**`rect`  
 [in]A [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)结构，它指定对话框的大小和位置。  
  
 `dwInitParam`  
 [in]指定要传递给的对话框中的值**lParam**参数**WM_INITDIALOG**消息。  
  
### <a name="return-value"></a>返回值  
 新创建的对话框句柄。  
  
### <a name="remarks"></a>备注  
 此对话框中会自动附加到`CDialogImpl`对象。 若要创建模式对话框，请调用[DoModal](#domodal)。 上面的第二个替代仅用于[CComControl](../../atl/reference/ccomcontrol-class.md)。  
  
##  <a name="destroywindow"></a>CDialogImpl::DestroyWindow  
 销毁无模式对话框。  
  
```  
 
BOOL DestroyWindow();

 
```  
  
### <a name="return-value"></a>返回值  
 **TRUE**如果对话框成功销毁; 否则为**FALSE**。  
  
### <a name="remarks"></a>备注  
 返回**TRUE**如果对话框成功销毁; 否则为**FALSE**。  
  
##  <a name="dialogproc"></a>CDialogImpl::DialogProc  
 此静态函数实现对话框过程。  
  
```  
 
static LRESULT CALLBACK DialogProc(
    HWND hWnd,  
    UINT uMsg,  
    WPARAM wParam,  
    LPARAM lParam);

 
```  
  
### <a name="parameters"></a>参数  
 `hWnd`  
 [in]对话框中句柄。  
  
 `uMsg`  
 [in]发送到对话框中的消息。  
  
 `wParam`  
 [in]消息特定的附加信息。  
  
 `lParam`  
 [in]消息特定的附加信息。  
  
### <a name="return-value"></a>返回值  
 **TRUE**如果消息已处理; 否则为**FALSE**。  
  
### <a name="remarks"></a>备注  
 `DialogProc`使用默认消息映射来将消息定向到相应的处理程序。  
  
 您可以重写`DialogProc`提供不同的机制，用于处理消息。  
  
##  <a name="domodal"></a>CDialogImpl::DoModal  
 创建模式对话框。  
  
```   
INT_PTR DoModal(  
    HWND hWndParent = ::GetActiveWindow(),   
    LPARAM dwInitParam = NULL); 
```  
  
### <a name="parameters"></a>参数  
 `hWndParent`  
 [in]向所有者窗口句柄。 默认值是返回值的[正在](http://msdn.microsoft.com/library/windows/desktop/ms646292)Win32 函数。  
  
 `dwInitParam`  
 [in]指定要传递给的对话框中的值**lParam**参数**WM_INITDIALOG**消息。  
  
### <a name="return-value"></a>返回值  
 如果成功，值`nRetCode`调用中指定的参数[EndDialog](#enddialog)。 否则为-1。  
  
### <a name="remarks"></a>备注  
 此对话框中会自动附加到`CDialogImpl`对象。  
  
 若要创建无模式对话框，请调用[创建](#create)。  
  
##  <a name="enddialog"></a>CDialogImpl::EndDialog  
 销毁模式对话框。  
  
```   
BOOL EndDialog(int nRetCode); 
```  
  
### <a name="parameters"></a>参数  
 `nRetCode`  
 [in]要返回的值[CDialogImpl::DoModal](#domodal)。  
  
### <a name="return-value"></a>返回值  
 **TRUE**的对话框是销毁; 否则为如果**FALSE**。  
  
### <a name="remarks"></a>备注  
 `EndDialog`必须通过对话框过程调用。 对话框时销毁后，Windows 使用的值`nRetCode`的返回值作为`DoModal`，其创建对话框。  
  
> [!NOTE]
>  不要调用`EndDialog`销毁无模式对话框。 调用[CWindow::DestroyWindow](../../atl/reference/cwindow-class.md#destroywindow)相反。  
  
##  <a name="getdialogproc"></a>CDialogImpl::GetDialogProc  
 返回`DialogProc`，当前对话框过程。  
  
```   
virtual WNDPROC GetDialogProc(); 
```  
  
### <a name="return-value"></a>返回值  
 当前的对话框过程。  
  
### <a name="remarks"></a>备注  
 重写此方法以将替换为你自己的对话框过程。  
  
##  <a name="mapdialogrect"></a>CDialogImpl::MapDialogRect  
 将转换 (maps) 到屏幕的指定矩形的对话框单位单位 （像素）。  
  
```   
BOOL MapDialogRect(LPRECT lpRect); 
```  
  
### <a name="parameters"></a>参数  
 `lpRect`  
 指向`CRect`对象或[RECT](../../mfc/reference/rect-structure1.md)结构，它将接收包含更新区域的更新的客户端坐标。  
  
### <a name="return-value"></a>返回值  
 如果更新才能成功; 则为非 0如果更新失败，则为 0。 若要获得扩展的错误信息，请调用 `GetLastError`。  
  
### <a name="remarks"></a>备注  
 该函数将在指定的坐标`RECT`结构使用转换后的坐标，这样，要用于创建对话框中，或将控件放在对话框中的结构。  
  
##  <a name="onfinalmessage"></a>CDialogImpl::OnFinalMessage  
 接收最后一条消息后调用 (通常`WM_NCDESTROY`)。  
  
```   
virtual void OnFinalMessage(HWND hWnd); 
```  
  
### <a name="parameters"></a>参数  
 `hWnd`  
 [in]正在销毁窗口的句柄。  
  
### <a name="remarks"></a>备注  
 请注意，是否你想要自动删除您在窗口析构时的对象，则可以调用`delete this;`此处。  
  
##  <a name="startdialogproc"></a>CDialogImpl::StartDialogProc  
 只能调用一次，第一个接收消息时，处理发送到对话框中的消息。  
  
```   
static LRESULT CALLBACK StartDialogProc(
    HWND hWnd,  
    UINT uMsg,  
    WPARAM wParam,  
    LPARAM lParam); 
```  
  
### <a name="parameters"></a>参数  
 `hWnd`  
 [in]对话框中句柄。  
  
 `uMsg`  
 [in]发送到对话框中的消息。  
  
 `wParam`  
 [in]消息特定的附加信息。  
  
 `lParam`  
 [in]消息特定的附加信息。  
  
### <a name="return-value"></a>返回值  
 窗口过程中。  
  
### <a name="remarks"></a>备注  
 首次调用后`StartDialogProc`，`DialogProc`是设置对话框过程中，并进一步调用转到此处。  
  
## <a name="see-also"></a>另请参阅  
 [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)   
 [类概述](../../atl/atl-class-overview.md)
