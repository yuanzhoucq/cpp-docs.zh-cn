---
title: CColorDialog 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CColorDialog
- AFXDLGS/CColorDialog
- AFXDLGS/CColorDialog::CColorDialog
- AFXDLGS/CColorDialog::DoModal
- AFXDLGS/CColorDialog::GetColor
- AFXDLGS/CColorDialog::GetSavedCustomColors
- AFXDLGS/CColorDialog::SetCurrentColor
- AFXDLGS/CColorDialog::OnColorOK
- AFXDLGS/CColorDialog::m_cc
dev_langs:
- C++
helpviewer_keywords:
- CColorDialog [MFC], CColorDialog
- CColorDialog [MFC], DoModal
- CColorDialog [MFC], GetColor
- CColorDialog [MFC], GetSavedCustomColors
- CColorDialog [MFC], SetCurrentColor
- CColorDialog [MFC], OnColorOK
- CColorDialog [MFC], m_cc
ms.assetid: d013dc25-9290-4b5d-a97e-95ad7208e13b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f0445939c7437e4978ee698005cc2f7541e6684b
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2018
ms.locfileid: "37339301"
---
# <a name="ccolordialog-class"></a>CColorDialog 类
可以将颜色选择对话框合并到应用程序。  
  
## <a name="syntax"></a>语法  
  
```  
class CColorDialog : public CCommonDialog  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CColorDialog::CColorDialog](#ccolordialog)|构造 `CColorDialog` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CColorDialog::DoModal](#domodal)|显示颜色对话框，并允许用户进行选择。|  
|[CColorDialog::GetColor](#getcolor)|返回`COLORREF`结构，它包含所选颜色的值。|  
|[CColorDialog::GetSavedCustomColors](#getsavedcustomcolors)|检索由用户创建的自定义颜色。|  
|[CColorDialog::SetCurrentColor](#setcurrentcolor)|强制将当前的颜色选择，为指定的颜色。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|描述|  
|----------|-----------------|  
|[CColorDialog::OnColorOK](#oncolorok)|重写以验证输入到对话框中的颜色。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CColorDialog::m_cc](#m_cc)|用于自定义对话框的设置的结构。|  
  
## <a name="remarks"></a>备注  
 一个`CColorDialog`对象是一个列表的显示系统定义颜色的对话框。 用户可以选择，或从列表中，随后报告该返回到应用程序对话框的退出时创建的特定颜色。  
  
 若要构造`CColorDialog`对象，使用提供的构造函数或类派生新类并使用你自己的自定义构造函数。  
  
 一旦对话框的构造完成后，可以设置或修改中的任何值[m_cc](#m_cc)结构来初始化对话框的控件的值。 *M_cc*结构的类型是[CHOOSECOLOR](http://msdn.microsoft.com/library/windows/desktop/ms646830)。  
  
 初始化对话框的控件之后, 调用`DoModal`成员函数以显示该对话框，并允许用户选择一种颜色。 `DoModal` 返回用户的选择的任一对话框中的确定 (IDOK) 或取消 (IDCANCEL) 按钮。  
  
 如果`DoModal`返回 IDOK，您可以使用其中一个`CColorDialog`的成员函数来检索用户输入的信息。  
  
 可以使用 Windows [CommDlgExtendedError](http://msdn.microsoft.com/library/windows/desktop/ms646916)函数来确定在对话框中的初始化过程中是否发生了错误并了解有关错误的详细信息。  
  
 `CColorDialog` 依赖于 COMMDLG。随 Windows 3.1 及更高版本的 DLL 文件。  
  
 若要自定义对话框中，派生的类从`CColorDialog`，提供自定义对话框模板，并添加消息映射来处理从扩展控件的通知消息。 任何未处理的消息应传递给类的基类。  
  
 不需要自定义挂钩函数。  
  
> [!NOTE]
>  在进行某些安装`CColorDialog`如果你已使用框架进行其他对象不会显示灰色背景`CDialog`对象灰色。  
  
 有关使用的详细信息`CColorDialog`，请参阅[通用对话框类](../../mfc/common-dialog-classes.md)  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 `CColorDialog`  
  
## <a name="requirements"></a>要求  
 **标头：** afxdlgs.h  
  
##  <a name="ccolordialog"></a>  CColorDialog::CColorDialog  
 构造 `CColorDialog` 对象。  
  
```  
CColorDialog(
    COLORREF clrInit = 0,  
    DWORD dwFlags = 0,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>参数  
 *clrInit*  
 默认颜色选择。 如果未不指定任何值，默认值为 RGB(0,0,0) （黑色）。  
  
 *dwFlags*  
 一组自定义的函数和外观对话框中的标志。 有关详细信息，请参阅[CHOOSECOLOR](http://msdn.microsoft.com/library/windows/desktop/ms646830) Windows SDK 中的结构。  
  
 *pParentWnd*  
 指向对话框的父级或所有者窗口的指针。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#49](../../mfc/codesnippet/cpp/ccolordialog-class_1.cpp)]  
  
##  <a name="domodal"></a>  CColorDialog::DoModal  
 调用此函数可显示 Windows 常见颜色对话框中，并允许用户选择一种颜色。  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>返回值  
 IDOK 或 IDCANCEL。 如果返回 IDCANCEL，则调用 Windows [CommDlgExtendedError](http://msdn.microsoft.com/library/windows/desktop/ms646916)函数来确定是否发生了错误。  
  
 IDOK 和 IDCANCEL 是常数，用于指示是否在用户选择了确定或取消按钮。  
  
### <a name="remarks"></a>备注  
 如果你想要通过设置的成员初始化的各种颜色对话框选项[m_cc](#m_cc)结构，应执行此操作之前调用`DoModal`但构造对话框对象之后。  
  
 在调用`DoModal`，可以调用其他成员函数来检索设置或用户的信息输入到对话框。  
  
### <a name="example"></a>示例  
  有关示例，请参阅[CColorDialog::CColorDialog](#ccolordialog)。  
  
##  <a name="getcolor"></a>  CColorDialog::GetColor  
 调用后调用此函数`DoModal`来检索有关用户所选的颜色的信息。  
  
```  
COLORREF GetColor() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个[COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)值，该值包含在颜色对话框中选择的颜色的 RGB 信息。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#50](../../mfc/codesnippet/cpp/ccolordialog-class_2.cpp)]  
  
##  <a name="getsavedcustomcolors"></a>  CColorDialog::GetSavedCustomColors  
 `CColorDialog` 对象允许用户，除了选择颜色，可以定义最多 16 个自定义颜色。  
  
```  
static COLORREF* PASCAL GetSavedCustomColors();
```  
  
### <a name="return-value"></a>返回值  
 指向将存储由用户创建的自定义颜色 16 个 RGB 颜色值的数组的指针。  
  
### <a name="remarks"></a>备注  
 `GetSavedCustomColors`成员函数提供了访问这些颜色。 完成后，可以检索到这些颜色[DoModal](#domodal)返回 IDOK。  
  
 每个返回的数组中的 16 RGB 值初始化为 RGB(255,255,255) （白色）。 仅在应用程序中的对话框框调用之间保存用户选择的自定义颜色。 如果你想要保存的应用程序的调用之间的这些颜色，则必须保存它们以某种其他方式，例如进行初始化 (。INI) 文件。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#51](../../mfc/codesnippet/cpp/ccolordialog-class_3.cpp)]  
  
##  <a name="m_cc"></a>  CColorDialog::m_cc  
 类型的结构[CHOOSECOLOR](http://msdn.microsoft.com/library/windows/desktop/ms646830)，其成员存储的特征和对话框中的值。  
  
```  
CHOOSECOLOR m_cc;  
```  
  
### <a name="remarks"></a>备注  
 构造后`CColorDialog`对象，可以使用*m_cc*若要设置之前，调用对话框中的各个方面[DoModal](#domodal)成员函数。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#53](../../mfc/codesnippet/cpp/ccolordialog-class_4.cpp)]  
  
##  <a name="oncolorok"></a>  CColorDialog::OnColorOK  
 重写以验证输入到对话框中的颜色。  
  
```  
virtual BOOL OnColorOK();
```  
  
### <a name="return-value"></a>返回值  
 如果不应取消对话框; 非零值否则为 0 以接受输入的颜色。  
  
### <a name="remarks"></a>备注  
 仅当你想要提供自定义验证的用户在颜色对话框中选择的颜色，重写此函数。  
  
 用户可以通过以下两种方法之一选择一种颜色：  
  
-   单击颜色调色板上的颜色。 所选的颜色的 RGB 值将反映相应的 RGB 编辑框中。  
  
-   RGB 中的输入值的编辑框  
  
 重写`OnColorOK`允许你拒绝用户到常见的颜色对话框中输入任何特定于应用程序的原因的颜色。  
  
 通常情况下，不需要使用此函数，因为框架提供的颜色的默认验证并显示一个消息框，如果输入无效的颜色。  
  
 您可以调用[SetCurrentColor](#setcurrentcolor)中`OnColorOK`强制颜色选择。 一次`OnColorOK`已激发 (即，用户单击**确定**以接受颜色更改)，可以调用[GetColor](#getcolor)以获取新颜色的 RGB 值。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#52](../../mfc/codesnippet/cpp/ccolordialog-class_5.cpp)]  
  
##  <a name="setcurrentcolor"></a>  CColorDialog::SetCurrentColor  
 调用此函数后调用`DoModal`若要强制当前颜色选择中指定的颜色值*clr*。  
  
```  
void SetCurrentColor(COLORREF clr);
```  
  
### <a name="parameters"></a>参数  
 *clr*  
 RGB 颜色值。  
  
### <a name="remarks"></a>备注  
 此函数从内部消息处理程序调用或`OnColorOK`。 对话框的将自动更新用户的选择值的基础*clr*参数。  
  
### <a name="example"></a>示例  
  有关示例，请参阅[CColorDialog::OnColorOK](#oncolorok)。  
  
## <a name="see-also"></a>请参阅  
 [MFC 示例 MDI](../../visual-cpp-samples.md)   
 [MFC 示例 DRAWCLI](../../visual-cpp-samples.md)   
 [CCommonDialog 类](../../mfc/reference/ccommondialog-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)

