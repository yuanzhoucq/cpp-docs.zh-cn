---
title: CMFCEditBrowseCtrl 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCEditBrowseCtrl
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::EnableBrowseButton
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::EnableFileBrowseButton
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::EnableFolderBrowseButton
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::GetMode
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::OnAfterUpdate
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::OnBrowse
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::OnChangeLayout
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::OnDrawBrowseButton
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::OnIllegalFileName
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::SetBrowseButtonImage
dev_langs:
- C++
helpviewer_keywords:
- CMFCEditBrowseCtrl [MFC], EnableBrowseButton
- CMFCEditBrowseCtrl [MFC], EnableFileBrowseButton
- CMFCEditBrowseCtrl [MFC], EnableFolderBrowseButton
- CMFCEditBrowseCtrl [MFC], GetMode
- CMFCEditBrowseCtrl [MFC], OnAfterUpdate
- CMFCEditBrowseCtrl [MFC], OnBrowse
- CMFCEditBrowseCtrl [MFC], OnChangeLayout
- CMFCEditBrowseCtrl [MFC], OnDrawBrowseButton
- CMFCEditBrowseCtrl [MFC], OnIllegalFileName
- CMFCEditBrowseCtrl [MFC], SetBrowseButtonImage
ms.assetid: 69cfd886-3d35-4bee-8901-7c88fcf9520f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2d00488a7e9a87116317aec35c82b73b40077d8c
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/05/2018
ms.locfileid: "37854003"
---
# <a name="cmfceditbrowsectrl-class"></a>CMFCEditBrowseCtrl 类
`CMFCEditBrowseCtrl`类支持编辑浏览控件，它是有选择性地包含浏览按钮可编辑文本框。 当用户单击浏览按钮时，此控件会执行自定义操作或显示包含文件浏览器或文件夹浏览器的标准对话框。  
  
## <a name="syntax"></a>语法  
  
```  
class CMFCEditBrowseCtrl : public CEdit  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|`CMFCEditBrowseCtrl::CMFCEditBrowseCtrl`|默认构造函数。|  
|`CMFCEditBrowseCtrl::~CMFCEditBrowseCtrl`|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[Cmfceditbrowsectrl:: Enablebrowsebutton](#enablebrowsebutton)|启用或禁用 （隐藏） 浏览按钮。|  
|[CMFCEditBrowseCtrl::EnableFileBrowseButton](#enablefilebrowsebutton)|使浏览按钮并将编辑浏览控件放入*文件浏览*模式。|  
|[CMFCEditBrowseCtrl::EnableFolderBrowseButton](#enablefolderbrowsebutton)|使浏览按钮并将编辑浏览控件放入*文件夹浏览*模式。|  
|[CMFCEditBrowseCtrl::GetMode](#getmode)|返回当前的浏览模式。|  
|[CMFCEditBrowseCtrl::OnAfterUpdate](#onafterupdate)|编辑浏览控件更新浏览操作结果后，由框架调用。|  
|[CMFCEditBrowseCtrl::OnBrowse](#onbrowse)|在用户单击浏览按钮后，由框架调用。|  
|[CMFCEditBrowseCtrl::OnChangeLayout](#onchangelayout)|重绘当前编辑浏览控件。|  
|[CMFCEditBrowseCtrl::OnDrawBrowseButton](#ondrawbrowsebutton)|由框架调用以绘制浏览按钮。|  
|[CMFCEditBrowseCtrl::OnIllegalFileName](#onillegalfilename)|当编辑控件中输入文件名非法时由框架调用。|  
|`CMFCEditBrowseCtrl::PreTranslateMessage`|将窗口消息调度到之前[TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955)并[DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) Windows 函数。 有关语法和详细信息，请参阅[cwnd:: Pretranslatemessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)。|  
|[CMFCEditBrowseCtrl::SetBrowseButtonImage](#setbrowsebuttonimage)|设置自定义映像的浏览按钮。|  
  
## <a name="remarks"></a>备注  
 使用编辑浏览控件选择文件或文件夹名称。 （可选） 使用控件执行如自定义操作，以显示一个对话框。 你可以显示或不显示浏览按钮，并在按钮上应用自定义标签或图像。  
  
 *浏览模式*的编辑浏览控件将确定是否显示浏览按钮并单击该按钮时发生的操作。 有关详细信息，请参阅[GetMode](#getmode)方法。  
  
 `CMFCEditBrowseCtrl`类支持以下模式。  
  
 **自定义模式**  
 当用户单击浏览按钮时执行自定义操作。 例如，可以显示特定于应用程序的对话框。  
  
 **文件模式**  
 当用户单击浏览按钮显示标准文件选择对话框。  
  
 **文件夹模式下**  
 当用户单击浏览按钮时显示一个标准文件夹选择对话框。  
  
## <a name="how-to-specify-an-edit-browse-control"></a>操作说明： 指定编辑浏览控件  
 执行以下步骤将合并你的应用程序中的一个编辑浏览控件：  
  
1.  如果你想要实现自定义浏览模式下，派生您自己的类从`CMFCEditBrowseCtrl`类，然后重写[CMFCEditBrowseCtrl::OnBrowse](#onbrowse)方法。 在重写方法中，执行自定义浏览操作并使用结果更新编辑浏览控件。  
  
2.  嵌入是`CMFCEditBrowseCtrl`对象或父窗口对象的派生的编辑浏览控件对象。  
  
3.  如果您使用**类向导**若要创建一个对话框，添加一个编辑控件 ( `CEdit`) 到对话框窗体。 此外，添加一个变量来访问标头文件中的控件。 在标头文件中，将更改从变量的类型`CEdit`到`CMFCEditBrowseCtrl`。 编辑浏览控件将自动创建。 如果不使用**类向导**，添加`CMFCEditBrowseCtrl`变量标头文件，然后调用其`Create`方法。  
  
4.  如果向对话框添加编辑浏览控件，请使用**ClassWizard**工具来设置数据交换。  
  
5.  调用[EnableFolderBrowseButton](#enablefolderbrowsebutton)， [EnableFileBrowseButton](#enablefilebrowsebutton)，或[EnableBrowseButton](#enablebrowsebutton)方法来设置浏览模式，并显示浏览按钮。 调用[GetMode](#getmode)方法来获取当前浏览模式。  
  
6.  若要提供自定义映像的浏览按钮，调用[SetBrowseButtonImage](#setbrowsebuttonimage)方法或重写[OnDrawBrowseButton](#ondrawbrowsebutton)方法。  
  
7.  若要从编辑浏览控件中删除浏览按钮，调用[EnableBrowseButton](#enablebrowsebutton)方法替换*bEnable*参数设置为 FALSE。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CEdit](../../mfc/reference/cedit-class.md)  
  
 [CMFCEditBrowseCtrl](../../mfc/reference/cmfceditbrowsectrl-class.md)  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用这两种方法`CMFCEditBrowseCtrl`类：`EnableFolderBrowseButton`和`EnableFileBrowseButton`。 此示例摘自[新的控件示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_NewControls#6](../../mfc/reference/codesnippet/cpp/cmfceditbrowsectrl-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls#7](../../mfc/reference/codesnippet/cpp/cmfceditbrowsectrl-class_2.cpp)]  
  
## <a name="requirements"></a>要求  
 **标头：** afxeditbrowsectrl.h  
  
##  <a name="enablebrowsebutton"></a>  Cmfceditbrowsectrl:: Enablebrowsebutton  
 显示或不在当前编辑浏览控件上显示浏览按钮。  
  
```  
void EnableBrowseButton(
    BOOL bEnable=TRUE,  
    LPCTSTR szLabel=_T("..."));
```  
  
### <a name="parameters"></a>参数  
 *bEnable*  
 为 TRUE，则显示浏览按钮;如果为 FALSE，则不希望显示浏览按钮。 默认值为 TRUE。  
  
 *szLabel*  
 浏览按钮显示标签。 默认值是" **...**".  
  
### <a name="remarks"></a>备注  
 如果*bEnable*参数为 TRUE 时，实现一个自定义操作，以便在单击浏览按钮时执行。 若要实现自定义操作，从派生类`CMFCEditBrowseCtrl`类，然后重写其[OnBrowse](#onbrowse)方法。  
  
 如果*bEnable*参数为 TRUE，该控件的浏览模式`BrowseMode_Default`; 否则为浏览模式是`BrowseMode_None`。 浏览模式的详细信息，请参阅[GetMode](#getmode)方法。  
  
##  <a name="enablefilebrowsebutton"></a>  CMFCEditBrowseCtrl::EnableFileBrowseButton  
 当前的编辑浏览控件上显示浏览按钮并将控件放入*文件浏览*模式。  
  
```  
void EnableFileBrowseButton(
    LPCTSTR lpszDefExt=NULL,  
    LPCTSTR lpszFilter=NULL,  
    DWORD dwFlags = OFN_HIDEREADONLY | OFN_OVERWRITEPROMPT);
```  
  
### <a name="parameters"></a>参数  
 *lpszDefExt*  
 指定在文件选择对话框中使用的默认文件扩展名。 默认值为 NULL。  
  
 *lpszFilter*  
 指定在文件选择对话框中使用的默认筛选器字符串。 默认值为 NULL。  
  
 *dwFlags*  
 对话框标志。 默认值是 OFN_HIDEREADONLY 和 OFN_OVERWRITEPROMPT 的按位组合 (OR)。  
  
### <a name="remarks"></a>备注  
 当编辑浏览控件处于文件浏览模式，并且在用户单击浏览按钮时，该控件将显示标准文件选择对话框。  
  
 有关可用标志的完整列表，请参阅[OPENFILENAME 结构](https://msdn.microsoft.com/library/ms646839.aspx)。  
  
##  <a name="enablefolderbrowsebutton"></a>  CMFCEditBrowseCtrl::EnableFolderBrowseButton  
 当前的编辑浏览控件上显示浏览按钮并将控件放入*文件夹浏览*模式。  
  
```  
void EnableFolderBrowseButton();
```  
  
### <a name="remarks"></a>备注  
 当编辑浏览控件在文件夹浏览模式中，并且用户单击浏览按钮时，该控件将显示标准文件夹选择对话框。  
  
##  <a name="getmode"></a>  CMFCEditBrowseCtrl::GetMode  
 检索当前的编辑浏览控件浏览模式。  
  
```  
CMFCEditBrowseCtrl::BrowseMode GetMode() const;  
```  
  
### <a name="return-value"></a>返回值  
 指定的当前编辑模式的枚举值之一浏览控件。 浏览模式确定框架是否显示浏览按钮，并在用户单击该按钮时，会发生什么操作。  
  
 下表列出可能的返回值。  
  
|“值”|描述|  
|-----------|-----------------|  
|`BrowseMode_Default`|**自定义模式**。 执行程序员定义的操作。|  
|`BrowseMode_File`|**文件模式**。 显示标准文件浏览器对话框。|  
|`BrowseMode_Folder`|**文件夹模式下**。 显示标准文件夹浏览器对话框。|  
|`BrowseMode_None`|不显示浏览按钮。|  
  
### <a name="remarks"></a>备注  
 默认情况下`CMFCEditBrowseCtrl`对象初始化为`BrowseMode_None`模式。 修改使用浏览模式[cmfceditbrowsectrl:: Enablebrowsebutton](#enablebrowsebutton)， [CMFCEditBrowseCtrl::EnableFileBrowseButton](#enablefilebrowsebutton)，和[CMFCEditBrowseCtrl::EnableFolderBrowseButton](#enablefolderbrowsebutton)方法。  
  
##  <a name="onafterupdate"></a>  CMFCEditBrowseCtrl::OnAfterUpdate  
 编辑浏览控件更新浏览操作结果后，由框架调用。  
  
```  
virtual void OnAfterUpdate();
```  
  
### <a name="remarks"></a>备注  
 重写此方法在派生类来实现自定义操作中。  
  
##  <a name="onbrowse"></a>  CMFCEditBrowseCtrl::OnBrowse  
 用户单击编辑浏览控件的浏览按钮后，由框架调用。  
  
```  
virtual void OnBrowse();
```  
  
### <a name="remarks"></a>备注  
 使用此方法以执行自定义代码，当用户单击编辑浏览控件的浏览按钮。 派生您自己的类从`CMFCEditBrowseCtrl`类并重写其`OnBrowse`方法。 在该方法中，实现自定义浏览操作并 （可选） 更新编辑浏览控件文本框。 在应用程序中使用[EnableBrowseButton](#enablebrowsebutton)方法以将编辑浏览控件放在*自定义浏览*模式。  
  
##  <a name="onchangelayout"></a>  CMFCEditBrowseCtrl::OnChangeLayout  
 重绘当前编辑浏览控件。  
  
```  
virtual void OnChangeLayout();
```  
  
### <a name="remarks"></a>备注  
 浏览模式的编辑浏览控件发生更改时，框架将调用此方法。 有关详细信息，请参阅[CMFCEditBrowseCtrl::GetMode](#getmode)。  
  
##  <a name="ondrawbrowsebutton"></a>  CMFCEditBrowseCtrl::OnDrawBrowseButton  
 由框架调用以绘制编辑浏览控件上的浏览按钮。  
  
```  
virtual void OnDrawBrowseButton(
    CDC* pDC,  
    CRect rect,  
    BOOL bIsButtonPressed,  
    BOOL bIsButtonHot);
```  
  
### <a name="parameters"></a>参数  
 *pDC*  
 一个指向设备上下文的指针。  
  
 *rect*  
 浏览按钮的边框。  
  
 *bIsButtonPressed*  
 如果按下按钮; 则为 TRUE否则为 FALSE。  
  
 *bIsButtonHot*  
 如果该按钮将突出显示; 则为 TRUE否则为 FALSE。  
  
### <a name="remarks"></a>备注  
 重写此函数在派生类以自定义浏览按钮的外观。  
  
##  <a name="setbrowsebuttonimage"></a>  CMFCEditBrowseCtrl::SetBrowseButtonImage  
 编辑浏览控件的浏览按钮上设置自定义映像。  
  
```  
void SetBrowseButtonImage(
    HICON hIcon,  
    BOOL bAutoDestroy= TRUE);

 
void SetBrowseButtonImage(
    HBITMAP hBitmap,  
    BOOL bAutoDestroy= TRUE);  
  
void SetBrowseButtonImage(UINT uiBmpResId);
```  
  
### <a name="parameters"></a>参数  
 *hIcon*  
 图标的句柄。  
  
 *hBitmap*  
 位图的句柄。  
  
 *uiBmpResId*  
 位图的资源 ID。  
  
 *bAutoDestroy*  
 如果为 TRUE 时将退出此方法; 删除指定的图标或位图否则为 FALSE。 默认值为 TRUE。  
  
### <a name="remarks"></a>备注  
 使用此方法将自定义映像应用到浏览按钮。 默认情况下，该框架时，获取标准映像编辑浏览控件处于*文件浏览*或*文件夹浏览*模式。  
  
##  <a name="onillegalfilename"></a>  CMFCEditBrowseCtrl::OnIllegalFileName  
 当编辑控件中输入文件名非法时由框架调用。  
  
```  
virtual BOOL OnIllegalFileName(CString& strFileName);
```  
  
### <a name="parameters"></a>参数  
 *strFileName*  
 指定的非法文件名。  
  
### <a name="return-value"></a>返回值  
 如果此文件的名称不能进一步文件对话框将传递，则应返回 FALSE。 在这种情况下，焦点将重新设置为编辑控件和用户应继续编辑。 默认实现显示一个消息框，告知用户有关的非法文件名称，并返回 FALSE。 可以重写此方法中，更正文件名，并返回 TRUE，返回用于进一步处理。  
  
### <a name="remarks"></a>备注  
  
## <a name="see-also"></a>请参阅  
 [层次结构图表](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)
