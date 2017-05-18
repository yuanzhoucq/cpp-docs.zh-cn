---
title: "CColorDialog 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
- colors, dialog box
- dialog boxes, colors
- CColorDialog class
ms.assetid: d013dc25-9290-4b5d-a97e-95ad7208e13b
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: a8aee088aadbca18acda348c574c8f4b55d1ecbb
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="ccolordialog-class"></a>CColorDialog 类
允许您将颜色选择对话框合并到您的应用程序。  
  
## <a name="syntax"></a>语法  
  
```  
class CColorDialog : public CCommonDialog  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CColorDialog::CColorDialog](#ccolordialog)|构造 `CColorDialog` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CColorDialog::DoModal](#domodal)|显示颜色对话框中，并允许用户进行选择。|  
|[CColorDialog::GetColor](#getcolor)|返回**COLORREF**包含所选颜色的值的结构。|  
|[CColorDialog::GetSavedCustomColors](#getsavedcustomcolors)|检索由用户创建的自定义颜色。|  
|[CColorDialog::SetCurrentColor](#setcurrentcolor)|强制当前为指定的颜色的颜色选择。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|说明|  
|----------|-----------------|  
|[CColorDialog::OnColorOK](#oncolorok)|重写以验证输入到对话框中的颜色。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[CColorDialog::m_cc](#m_cc)|用于自定义设置对话框中的结构。|  
  
## <a name="remarks"></a>备注  
 一个`CColorDialog`对象是为显示系统定义的颜色列表具有的对话框。 用户可以选择，或从列表中，然后报告这些返回到应用程序对话框中退出时创建特定的颜色。  
  
 若要构造`CColorDialog`对象、 使用提供的构造函数或派生新类并使用您自己的自定义构造函数。  
  
 一旦构造的对话框中，您可以设置或修改中的任何值[m_cc](#m_cc)结构来初始化对话框的控件的值。 `m_cc`结构属于类型[CHOOSECOLOR](http://msdn.microsoft.com/library/windows/desktop/ms646830)。  
  
 初始化后对话框的控件，调用`DoModal`成员函数以显示对话框中，并让用户能够选择一种颜色。 `DoModal`返回用户所选的任何一个对话框的确定 ( **IDOK**) 或取消 ( **IDCANCEL**) 按钮。  
  
 如果`DoModal`返回**IDOK**，您可以使用其中一个`CColorDialog`的成员函数来检索用户输入的信息。  
  
 您可以使用 Windows [CommDlgExtendedError](http://msdn.microsoft.com/library/windows/desktop/ms646916)函数来确定在对话框中的初始化过程中是否发生了错误，以及若要了解有关错误的详细信息。  
  
 `CColorDialog`依赖于 COMMDLG。随 Windows 3.1 及更高版本一起提供的 DLL 文件。  
  
 要自定义对话框中，从派生类`CColorDialog`，提供自定义对话框模板上，并添加一个消息映射来处理来自扩展控件的通知消息。 任何未处理的消息应传递给类的基类。  
  
 不需要自定义挂钩函数。  
  
> [!NOTE]
>  在进行某些安装`CColorDialog`对象将不会显示带有灰色背景如果已使用该框架来进行其他`CDialog`对象灰色。  
  
 有关详细信息使用`CColorDialog`，请参阅[通用对话框类](../../mfc/common-dialog-classes.md)  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 `CColorDialog`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxdlgs.h  
  
##  <a name="ccolordialog"></a>CColorDialog::CColorDialog  
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
  
 `dwFlags`  
 一组自定义的函数和外观对话框中的标志。 有关详细信息，请参阅[CHOOSECOLOR](http://msdn.microsoft.com/library/windows/desktop/ms646830)结构中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `pParentWnd`  
 指向对话框中的父窗口或所有者窗口的指针。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView #&49;](../../mfc/codesnippet/cpp/ccolordialog-class_1.cpp)]  
  
##  <a name="domodal"></a>CColorDialog::DoModal  
 调用此函数可显示 Windows 常见颜色对话框中，并让用户能够选择一种颜色。  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>返回值  
 **IDOK**或**IDCANCEL**。 如果**IDCANCEL**是返回，调用 Windows [CommDlgExtendedError](http://msdn.microsoft.com/library/windows/desktop/ms646916)函数来确定是否发生了错误。  
  
 **IDOK**和**IDCANCEL**是常数，指示用户是否选择了确定或取消按钮。  
  
### <a name="remarks"></a>备注  
 如果您想要通过设置的成员初始化的各种颜色对话框中选项[m_cc](#m_cc)结构中，应执行此操作，然后再调`DoModal`但在构造对话框对象之后。  
  
 在调用`DoModal`，可调用其他成员函数来检索设置或用户的信息输入到对话框。  
  
### <a name="example"></a>示例  
  请参阅示例[CColorDialog::CColorDialog](#ccolordialog)。  
  
##  <a name="getcolor"></a>CColorDialog::GetColor  
 在调用后调用此函数`DoModal`来检索有关用户选定的颜色的信息。  
  
```  
COLORREF GetColor() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个[COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)值，该值包含在颜色对话框中选定的颜色的 RGB 信息。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView #&50;](../../mfc/codesnippet/cpp/ccolordialog-class_2.cpp)]  
  
##  <a name="getsavedcustomcolors"></a>CColorDialog::GetSavedCustomColors  
 `CColorDialog`对象允许用户，除了选择颜色，可以定义最多 16 个自定义颜色。  
  
```  
static COLORREF* PASCAL GetSavedCustomColors();
```  
  
### <a name="return-value"></a>返回值  
 指向将存储由用户创建的自定义颜色 16 RGB 颜色值的数组的指针。  
  
### <a name="remarks"></a>备注  
 `GetSavedCustomColors`成员函数提供对这些颜色的访问。 这些颜色可以后检索到[DoModal](#domodal)返回**IDOK**。  
  
 每个返回的数组中的 16 RGB 值初始化为 RGB(255,255,255) （白色）。 应用程序中的对话框框中调用之间仅保存用户所选择的自定义颜色。 如果您想要保存这些应用程序的调用之间的颜色，则必须保存这些以某种其他方式，如进行初始化 (。INI) 文件。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView #&51;](../../mfc/codesnippet/cpp/ccolordialog-class_3.cpp)]  
  
##  <a name="m_cc"></a>CColorDialog::m_cc  
 类型的结构[CHOOSECOLOR](http://msdn.microsoft.com/library/windows/desktop/ms646830)，其成员存储的特征和对话框中的值。  
  
```  
CHOOSECOLOR m_cc;  
```  
  
### <a name="remarks"></a>备注  
 在构造之后`CColorDialog`对象，可以使用`m_cc`设置之前，先调用对话框中的各个方面[DoModal](#domodal)成员函数。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView #&53;](../../mfc/codesnippet/cpp/ccolordialog-class_4.cpp)]  
  
##  <a name="oncolorok"></a>CColorDialog::OnColorOK  
 重写以验证输入到对话框中的颜色。  
  
```  
virtual BOOL OnColorOK();
```  
  
### <a name="return-value"></a>返回值  
 非零，如果不应消除对话框中;否则为 0 表示接受输入的颜色。  
  
### <a name="remarks"></a>备注  
 仅当您想要提供自定义验证的用户在颜色对话框中选择的颜色，重写此函数。  
  
 用户可以通过以下两种方法之一来选择一种颜色︰  
  
-   单击颜色调色板上的颜色。 所选的颜色的 RGB 值将反映在相应的 RGB 编辑框中。  
  
-   RGB 中的输入值的编辑框  
  
 重写`OnColorOK`允许您拒绝用户到一个公共的颜色对话框中输入任何应用程序特定原因的颜色。  
  
 通常情况下，不需要使用此函数，因为框架提供的颜色的默认验证并显示一个消息框，如果输入无效的颜色。  
  
 您可以调用[SetCurrentColor](#setcurrentcolor)中`OnColorOK`强制颜色选择。 一次`OnColorOK`已激发 (也就是说，用户单击**确定**接受颜色更改)，您可以调用[GetColor](#getcolor)来获取新的颜色的 RGB 值。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView #&52;](../../mfc/codesnippet/cpp/ccolordialog-class_5.cpp)]  
  
##  <a name="setcurrentcolor"></a>CColorDialog::SetCurrentColor  
 在调用后调用此函数`DoModal`强制中指定的颜色值的当前颜色选定`clr`。  
  
```  
void SetCurrentColor(COLORREF clr);
```  
  
### <a name="parameters"></a>参数  
 `clr`  
 RGB 颜色值。  
  
### <a name="remarks"></a>备注  
 此函数从内部调用消息处理程序或`OnColorOK`。 对话框中将自动更新基于值的用户的选择`clr`参数。  
  
### <a name="example"></a>示例  
  请参阅示例[CColorDialog::OnColorOK](#oncolorok)。  
  
## <a name="see-also"></a>另请参阅  
 [MFC 示例 MDI](../../visual-cpp-samples.md)   
 [MFC 示例 DRAWCLI](../../visual-cpp-samples.md)   
 [CCommonDialog 类](../../mfc/reference/ccommondialog-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)


