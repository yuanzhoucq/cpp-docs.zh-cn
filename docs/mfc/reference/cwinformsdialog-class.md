---
title: CWinFormsDialog 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CWinFormsDialog
- AFXWINFORMS/CWinFormsDialog
- AFXWINFORMS/CWinFormsDialog::CWinFormsDialog
- AFXWINFORMS/CWinFormsDialog::GetControl
- AFXWINFORMS/CWinFormsDialog::GetControlHandle
- AFXWINFORMS/CWinFormsDialog::OnInitDialog
dev_langs:
- C++
helpviewer_keywords:
- CWinFormsDialog [MFC], CWinFormsDialog
- CWinFormsDialog [MFC], GetControl
- CWinFormsDialog [MFC], GetControlHandle
- CWinFormsDialog [MFC], OnInitDialog
ms.assetid: e3cec000-a578-448e-b06a-8af256312f61
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 69882f9b22d11de139951b6196b58729af70a36a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46018140"
---
# <a name="cwinformsdialog-class"></a>CWinFormsDialog 类
承载 Windows 窗体用户控件的 MFC 对话框类的包装器。  
  
## <a name="syntax"></a>语法  
  
```  
template <typename TManagedControl>  
class CWinFormsDialog :   
    public CDialog  
```  
  
#### <a name="parameters"></a>参数  
*TManagedControl*<br/>
要显示在 MFC 应用程序的.NET Framework 用户控件。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CWinFormsDialog::CWinFormsDialog](#cwinformsdialog)|构造 `CWinFormsDialog` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CWinFormsDialog::GetControl](#getcontrol)|检索对 Windows 窗体用户控件的引用。|  
|[CWinFormsDialog::GetControlHandle](#getcontrolhandle)|检索 Windows 窗体用户控件的窗口句柄。|  
|[CWinFormsDialog::OnInitDialog](#oninitdialog)|通过创建并承载 Windows 窗体用户控件对其初始化 MFC 对话框。|  
  
### <a name="public-operators"></a>公共运算符  
  
|name||  
|----------|-|  
|[CWinFormsDialog::operator-&gt;](#operator_-_gt)|将替换[CWinFormsDialog::GetControl](#getcontrol)在表达式中。|  
|[CWinFormsDialog::operator TManagedControl ^](#operator_tmanagedcontrol)|将一种类型强制转换为对 Windows 窗体用户控件的引用。|  
  
## <a name="remarks"></a>备注  
 `CWinFormsDialog` 是的 MFC 对话框类的包装器 ( [CDialog](../../mfc/reference/cdialog-class.md)) 承载 Windows 窗体用户控件。 这允许.NET Framework 上的控件模式或无模式 MFC 对话框中显示。  
  
 有关使用 Windows 窗体的详细信息，请参阅[在 MFC 中使用 Windows 窗体用户控件](../../dotnet/using-a-windows-form-user-control-in-mfc.md)并[承载 Windows 窗体用户控件作为 MFC 对话框](../../dotnet/hosting-a-windows-form-user-control-as-an-mfc-dialog-box.md)。  
  
## <a name="requirements"></a>要求  
 **标头：** afxwinforms.h  
  
##  <a name="cwinformsdialog"></a>  CWinFormsDialog::CWinFormsDialog  
 构造 `CWinFormsDialog` 对象。  
  
```  
CWinFormsDialog(UINT nIDTemplate = IDD);
```  
  
### <a name="parameters"></a>参数  
 *nIDTemplate*  
 包含对话框模板资源的 ID。 使用对话框编辑器创建对话框模板并将其存储在应用程序的资源脚本文件中。 对话框模板的详细信息，请参阅[CDialog 类](../../mfc/reference/cdialog-class.md)。  
  
##  <a name="getcontrol"></a>  CWinFormsDialog::GetControl  
 检索对 Windows 窗体用户控件的引用。  
  
```  
inline TManagedControl^ GetControl() const;  
```  
  
### <a name="return-value"></a>返回值  
 在 MFC 对话框中返回到 Windows 窗体控件的引用。  
  
##  <a name="getcontrolhandle"></a>  CWinFormsDialog::GetControlHandle  
 检索 Windows 窗体用户控件的窗口句柄。  
  
```  
inline HWND GetControlHandle() const throw();
```  
  
### <a name="return-value"></a>返回值  
 返回 Windows 窗体用户控件的窗口句柄。  
  
##  <a name="oninitdialog"></a>  CWinFormsDialog::OnInitDialog  
 通过创建并承载 Windows 窗体用户控件对其初始化 MFC 对话框。  
  
```  
virtual BOOL OnInitDialog();
```  
  
### <a name="return-value"></a>返回值  
 一个布尔值，该值指定是否应用程序已将输入的焦点设置到其中一个控件在对话框中。 如果`OnInitDialog`返回非零值时，Windows 将输入的焦点设置到的第一个控件在对话框中。 仅当应用程序具有显式将输入的焦点设置到其中一个控件在对话框中，此方法可以返回 0。  
  
### <a name="remarks"></a>备注  
 创建 MFC 对话框中时 (使用[创建](../../mfc/reference/cdialog-class.md#create)， [CreateIndirect](../../mfc/reference/cdialog-class.md#createindirect)，或[DoModal](../../mfc/reference/cdialog-class.md#domodal)方法继承自[CDialog](../../mfc/reference/cdialog-class.md))，WM_发送 INITDIALOG 消息并调用此方法。 它创建对话框上的 Windows 窗体控件的实例，并调整大小以适应用户控件的大小的对话框。 然后，它托管在 MFC 对话框中的新控件。  
  
 如果您需要执行特殊处理对话框的初始化时，重写此成员函数。 使用此方法的详细信息，请参阅[CDialog::OnInitDialog](../../mfc/reference/cdialog-class.md#oninitdialog)。  
  
##  <a name="operator_-_gt"></a>  CWinFormsDialog::operator-&gt;  
 将替换[CWinFormsDialog::GetControl](#getcontrol)在表达式中。  
  
```  
inline TManagedControl^  operator->() const throw();
```  
  
### <a name="remarks"></a>备注  
 此运算符提供了方便的语法，用于替换`GetControl`在表达式中。  
  
 有关使用 Windows 窗体的信息，请参阅[在 MFC 中使用 Windows 窗体用户控件](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。  
  
##  <a name="operator_tmanagedcontrol_xor"></a>  CWinFormsDialog::operator TManagedControl ^  
 将一种类型强制转换为对 Windows 窗体用户控件的引用。  
  
```  
inline operator TManagedControl^() const throw();
```  
  
### <a name="remarks"></a>备注  
 此运算符将一种类型强制转换为对 Windows 窗体控件的引用。 用于将传递`CWinFormsDialog<TManagedControl>`对话框，以便接受到 Windows 窗体用户控件对象的指针的函数。  
  
## <a name="see-also"></a>请参阅  
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [CWinFormsView 类](../../mfc/reference/cwinformsview-class.md)   
 [CDialog 类](../../mfc/reference/cdialog-class.md)
