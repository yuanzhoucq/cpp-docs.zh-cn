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
- ATL.CDialogImpl
- ATL::CDialogImpl
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 732227ef8566ce5e2985a3e65a1153a130df6b20
ms.lasthandoff: 02/24/2017

---
# <a name="cdialogimpl-class"></a>CDialogImpl 类
此类提供用于创建模式或无模式对话框的方法。  
  
> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类及其成员。  
  
## <a name="syntax"></a>语法  
  
```  
 
template <class T,  
    class TBase = CWindow>  
    class ATL_NO_VTABLE CDialogImpl : public CDialogImplBaseT<TBase>  
 
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 您的类，派生自`CDialogImpl`。  
  
 *TBase*  
 您的新类的基类。 默认基类为[CWindow](../../atl/reference/cwindow-class.md)。  
  
## <a name="members"></a>成员  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[创建](#create)|创建无模式对话框。|  
|[DestroyWindow](#destroywindow)|销毁无模式对话框。|  
|[DoModal](#domodal)|创建模式对话框。|  
|[EndDialog](#enddialog)|销毁一个模式对话框。|  
  
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
 与`CDialogImpl`可以创建一个模式对话框或无模式对话框。 `CDialogImpl`提供了对话框过程，使用默认消息映射将消息定向到相应的处理程序。  
  
 基类析构函数**~ CWindowImplRoot**可确保在销毁对象之前是否已删除窗口中。  
  
 `CDialogImpl`派生自**CDialogImplBaseT**，它又派生自**CWindowImplRoot**。  
  
> [!NOTE]
>  您的类必须定义**IDD**成员，用于指定对话框模板资源 id。 例如，ATL 项目向导自动将以下行添加到您的类︰  
  
 [!code-cpp[NVC_ATL_Windowing #&41;](../../atl/codesnippet/cpp/cdialogimpl-class_1.h)]  
  
 其中`MyDlg`是**短名称**输入到向导中**名称**页。  
  
|有关以下内容的详细信息|请参阅|  
|--------------------------------|---------|  
|创建控件|[ATL 教程](../../atl/active-template-library-atl-tutorial.md)|  
|使用 ATL 中的对话框|[ATL 窗口类](../../atl/atl-window-classes.md)|  
|ATL 项目向导|[创建 ATL 项目](../../atl/reference/creating-an-atl-project.md)|  
|对话框|[对话框](http://msdn.microsoft.com/library/windows/desktop/ms632588)和后续主题中的[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]|  
  
## <a name="requirements"></a>要求  
 **标头︰** atlwin.h  
  
##  <a name="a-namecreatea--cdialogimplcreate"></a><a name="create"></a>CDialogImpl::Create  
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
 [in]所有者窗口的句柄。  
  
 **RECT &**`rect`  
 [in]一个[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)结构，它指定对话框的大小和位置。  
  
 `dwInitParam`  
 [in]指定要传递给对话框中的值**lParam**参数**WM_INITDIALOG**消息。  
  
### <a name="return-value"></a>返回值  
 指向新建对话框中的句柄。  
  
### <a name="remarks"></a>备注  
 此对话框中会自动附加到`CDialogImpl`对象。 若要创建模式对话框，请调用[DoModal](#domodal)。 上面的第二个重写仅用于[CComControl](../../atl/reference/ccomcontrol-class.md)。  
  
##  <a name="a-namedestroywindowa--cdialogimpldestroywindow"></a><a name="destroywindow"></a>CDialogImpl::DestroyWindow  
 销毁无模式对话框。  
  
```  
 
BOOL DestroyWindow();

 
```  
  
### <a name="return-value"></a>返回值  
 **TRUE**如果对话框已成功地销毁; 否则为**FALSE**。  
  
### <a name="remarks"></a>备注  
 返回**TRUE**如果对话框已成功地销毁; 否则为**FALSE**。  
  
##  <a name="a-namedialogproca--cdialogimpldialogproc"></a><a name="dialogproc"></a>CDialogImpl::DialogProc  
 此静态函数可实现对话框过程。  
  
```  
 
static LRESULT CALLBACK DialogProc(
    HWND hWnd,  
    UINT uMsg,  
    WPARAM wParam,  
    LPARAM lParam);

 
```  
  
### <a name="parameters"></a>参数  
 `hWnd`  
 [in]指向对话框中的句柄。  
  
 `uMsg`  
 [in]发送到对话框中的消息。  
  
 `wParam`  
 [in]消息特定的附加信息。  
  
 `lParam`  
 [in]消息特定的附加信息。  
  
### <a name="return-value"></a>返回值  
 **TRUE**如果消息已处理; 否则为**FALSE**。  
  
### <a name="remarks"></a>备注  
 `DialogProc`使用默认消息映射将消息定向到相应的处理程序。  
  
 您可以重写`DialogProc`提供另一种机制来处理消息。  
  
##  <a name="a-namedomodala--cdialogimpldomodal"></a><a name="domodal"></a>CDialogImpl::DoModal  
 创建模式对话框。  
  
```   
INT_PTR DoModal(  
    HWND hWndParent = ::GetActiveWindow(),   
    LPARAM dwInitParam = NULL); 
```  
  
### <a name="parameters"></a>参数  
 `hWndParent`  
 [in]所有者窗口的句柄。 默认值是返回值的[正在](http://msdn.microsoft.com/library/windows/desktop/ms646292)Win32 函数。  
  
 `dwInitParam`  
 [in]指定要传递给对话框中的值**lParam**参数**WM_INITDIALOG**消息。  
  
### <a name="return-value"></a>返回值  
 如果成功，值`nRetCode`对调用中指定的参数[EndDialog](#enddialog)。 否则为-1。  
  
### <a name="remarks"></a>备注  
 此对话框中会自动附加到`CDialogImpl`对象。  
  
 若要创建无模式对话框，请调用[创建](#create)。  
  
##  <a name="a-nameenddialoga--cdialogimplenddialog"></a><a name="enddialog"></a>CDialogImpl::EndDialog  
 销毁一个模式对话框。  
  
```   
BOOL EndDialog(int nRetCode); 
```  
  
### <a name="parameters"></a>参数  
 `nRetCode`  
 [in]通过返回的值[CDialogImpl::DoModal](#domodal)。  
  
### <a name="return-value"></a>返回值  
 **TRUE**对话框中是否已损坏; 否则为**FALSE**。  
  
### <a name="remarks"></a>备注  
 `EndDialog`必须通过对话框过程调用。 对话框中被销毁后，Windows 将使用的值`nRetCode`的返回值作为`DoModal`，其创建对话框。  
  
> [!NOTE]
>  不要调用`EndDialog`要销毁的无模式对话框。 调用[CWindow::DestroyWindow](../../atl/reference/cwindow-class.md#destroywindow)相反。  
  
##  <a name="a-namegetdialogproca--cdialogimplgetdialogproc"></a><a name="getdialogproc"></a>CDialogImpl::GetDialogProc  
 返回`DialogProc`，当前对话框过程。  
  
```   
virtual WNDPROC GetDialogProc(); 
```  
  
### <a name="return-value"></a>返回值  
 当前的对话框过程。  
  
### <a name="remarks"></a>备注  
 重写此方法，以替换为您自己的对话框过程。  
  
##  <a name="a-namemapdialogrecta--cdialogimplmapdialogrect"></a><a name="mapdialogrect"></a>CDialogImpl::MapDialogRect  
 将转换 （映射） 到屏幕的指定矩形的对话框单位单位 （像素）。  
  
```   
BOOL MapDialogRect(LPRECT lpRect); 
```  
  
### <a name="parameters"></a>参数  
 `lpRect`  
 指向`CRect`对象或[RECT](../../mfc/reference/rect-structure1.md)结构，它是用于接收包含更新区域的更新的客户端坐标。  
  
### <a name="return-value"></a>返回值  
 如果更新成功，则非零值如果更新失败，则为 0。 若要获得扩展的错误信息，请调用 `GetLastError`。  
  
### <a name="remarks"></a>备注  
 函数将替换为在指定的坐标`RECT`结构使用转换后的坐标，这样，要使用创建对话框，或将控件放在对话框中的结构。  
  
##  <a name="a-nameonfinalmessagea--cdialogimplonfinalmessage"></a><a name="onfinalmessage"></a>CDialogImpl::OnFinalMessage  
 接收最后一条消息后调用 (通常`WM_NCDESTROY`)。  
  
```   
virtual void OnFinalMessage(HWND hWnd); 
```  
  
### <a name="parameters"></a>参数  
 `hWnd`  
 [in]销毁窗口的句柄。  
  
### <a name="remarks"></a>备注  
 请注意，是否您想要自动删除您的对象在窗口析构时，您可以调用`delete this;`此处。  
  
##  <a name="a-namestartdialogproca--cdialogimplstartdialogproc"></a><a name="startdialogproc"></a>CDialogImpl::StartDialogProc  
 只调用一次，第一条消息收到时，用于处理发送到对话框中的消息。  
  
```   
static LRESULT CALLBACK StartDialogProc(
    HWND hWnd,  
    UINT uMsg,  
    WPARAM wParam,  
    LPARAM lParam); 
```  
  
### <a name="parameters"></a>参数  
 `hWnd`  
 [in]指向对话框中的句柄。  
  
 `uMsg`  
 [in]发送到对话框中的消息。  
  
 `wParam`  
 [in]消息特定的附加信息。  
  
 `lParam`  
 [in]消息特定的附加信息。  
  
### <a name="return-value"></a>返回值  
 窗口过程。  
  
### <a name="remarks"></a>备注  
 在首次调用后`StartDialogProc`，`DialogProc`是设置对话框过程中，并进一步调用转到此处。  
  
## <a name="see-also"></a>另请参阅  
 [BEGIN_MSG_MAP](http://msdn.microsoft.com/library/8bbb5af9-18b1-48c6-880e-166f599ee554)   
 [类概述](../../atl/atl-class-overview.md)
