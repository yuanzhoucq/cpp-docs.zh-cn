---
title: "CMFCEditBrowseCtrl 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCEditBrowseCtrl
dev_langs:
- C++
helpviewer_keywords:
- CMFCEditBrowseCtrl::PreTranslateMessage method
- CMFCEditBrowseCtrl constructor
- CMFCEditBrowseCtrl class
ms.assetid: 69cfd886-3d35-4bee-8901-7c88fcf9520f
caps.latest.revision: 33
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
ms.openlocfilehash: 5c5650da677a442628049c9ef4b41c2142cfb2c2
ms.lasthandoff: 02/24/2017

---
# <a name="cmfceditbrowsectrl-class"></a>CMFCEditBrowseCtrl 类
`CMFCEditBrowseCtrl`类支持编辑浏览控件，它是有选择性地包含浏览按钮可编辑文本框。 当用户单击浏览按钮时，此控件会执行自定义操作或显示包含文件浏览器或文件夹浏览器的标准对话框。  
  
## <a name="syntax"></a>语法  
  
```  
class CMFCEditBrowseCtrl : public CEdit  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|`CMFCEditBrowseCtrl::CMFCEditBrowseCtrl`|默认构造函数。|  
|`CMFCEditBrowseCtrl::~CMFCEditBrowseCtrl`|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CMFCEditBrowseCtrl::EnableBrowseButton](#enablebrowsebutton)|启用或禁用 （隐藏） 浏览按钮。|  
|[CMFCEditBrowseCtrl::EnableFileBrowseButton](#enablefilebrowsebutton)|使浏览按钮并将编辑浏览控件放入*文件浏览*模式。|  
|[CMFCEditBrowseCtrl::EnableFolderBrowseButton](#enablefolderbrowsebutton)|使浏览按钮并将编辑浏览控件放入*文件夹浏览*模式。|  
|[CMFCEditBrowseCtrl::GetMode](#getmode)|返回当前的浏览模式。|  
|[CMFCEditBrowseCtrl::OnAfterUpdate](#onafterupdate)|编辑浏览控件更新用的浏览操作的结果后，由框架调用。|  
|[CMFCEditBrowseCtrl::OnBrowse](#onbrowse)|在用户单击浏览按钮之后，由框架调用。|  
|[CMFCEditBrowseCtrl::OnChangeLayout](#onchangelayout)|重绘当前编辑浏览控件。|  
|[CMFCEditBrowseCtrl::OnDrawBrowseButton](#ondrawbrowsebutton)|由框架来绘制浏览按钮调用。|  
|[CMFCEditBrowseCtrl::OnIllegalFileName](#onillegalfilename)|在编辑控件中输入了非法的文件名称时，由框架调用。|  
|`CMFCEditBrowseCtrl::PreTranslateMessage`|翻译窗口消息之前被发送到[TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955)和[DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) Windows 函数。 有关语法和详细信息，请参阅[cwnd:: Pretranslatemessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)。|  
|[CMFCEditBrowseCtrl::SetBrowseButtonImage](#setbrowsebuttonimage)|设置自定义映像的浏览按钮。|  
  
## <a name="remarks"></a>备注  
 使用编辑浏览控件选择文件或文件夹名称。 （可选） 使用该控件才能执行如自定义操作显示的对话框。 你可以显示或不显示浏览按钮，并在按钮上应用的自定义标签或图像。  
  
 *浏览模式*的编辑浏览控件将确定是否显示浏览按钮并单击按钮时，会发生何种操作。 有关详细信息，请参阅[GetMode](#getmode)方法。  
  
 `CMFCEditBrowseCtrl`类支持以下模式。  
  
 `custom mode`  
 在用户单击浏览按钮时执行自定义操作。 例如，可以显示特定于应用程序的对话框。  
  
 `file mode`  
 当用户单击浏览按钮，将显示标准文件选择对话框。  
  
 `folder mode`  
 当用户单击浏览按钮，将显示一个标准文件夹选择对话框。  
  
## <a name="how-to-specify-an-edit-browse-control"></a>如何︰ 指定编辑浏览控件  
 执行以下步骤以将应用程序中的编辑浏览控件合并︰  
  
1.  如果您想要实现自定义浏览模式下，派生您自己的类从`CMFCEditBrowseCtrl`类，然后重写[CMFCEditBrowseCtrl::OnBrowse](#onbrowse)方法。 在重写方法中，执行自定义浏览操作，并使用结果更新编辑浏览控件。  
  
2.  嵌入任何一个`CMFCEditBrowseCtrl`对象或父窗口对象的派生的编辑浏览控件对象。  
  
3.  如果您使用**类向导**若要创建一个对话框中，添加一个编辑控件 ( `CEdit`) 到对话框的窗体。 此外，添加一个变量来访问标头文件中的控件。 在标头文件中，将从变量的类型更改`CEdit`到`CMFCEditBrowseCtrl`。 编辑浏览控件将自动创建。 如果不使用**类向导**，添加`CMFCEditBrowseCtrl`变量与头文件，然后调用其`Create`方法。  
  
4.  如果将编辑浏览控件添加到对话框中，使用**ClassWizard**工具来设置数据交换。  
  
5.  调用[EnableFolderBrowseButton](#enablefolderbrowsebutton)， [EnableFileBrowseButton](#enablefilebrowsebutton)，或[EnableBrowseButton](#enablebrowsebutton)方法来设置浏览模式并显示浏览按钮。 调用[GetMode](#getmode)方法来获取当前的浏览模式。  
  
6.  若要为浏览按钮提供自定义映像，请调用[SetBrowseButtonImage](#setbrowsebuttonimage)方法或重写[OnDrawBrowseButton](#ondrawbrowsebutton)方法。  
  
7.  若要从编辑浏览控件中删除浏览按钮，调用[EnableBrowseButton](#enablebrowsebutton)方法`bEnable`参数设置为`FALSE`。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CEdit](../../mfc/reference/cedit-class.md)  
  
 [CMFCEditBrowseCtrl](../../mfc/reference/cmfceditbrowsectrl-class.md)  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用这两种方法`CMFCEditBrowseCtrl`类︰`EnableFolderBrowseButton`和`EnableFileBrowseButton`。 此示例摘自[新控件示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_NewControls #&6;](../../mfc/reference/codesnippet/cpp/cmfceditbrowsectrl-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls #&7;](../../mfc/reference/codesnippet/cpp/cmfceditbrowsectrl-class_2.cpp)]  
  
## <a name="requirements"></a>要求  
 **标头︰** afxeditbrowsectrl.h  
  
##  <a name="a-nameenablebrowsebuttona--cmfceditbrowsectrlenablebrowsebutton"></a><a name="enablebrowsebutton"></a>CMFCEditBrowseCtrl::EnableBrowseButton  
 显示或不在当前的编辑浏览控件上显示浏览按钮。  
  
```  
void EnableBrowseButton(
    BOOL bEnable=TRUE,  
    LPCTSTR szLabel=_T("..."));
```  
  
### <a name="parameters"></a>参数  
 `bEnable`  
 `TRUE`若要显示浏览按钮;`FALSE`不希望显示浏览按钮。 默认值为 `TRUE`。  
  
 `szLabel`  
 在浏览按钮显示标签。 默认值是" **...**".  
  
### <a name="remarks"></a>备注  
 如果`bEnable`参数是`TRUE`，实现一个自定义操作，以便在单击浏览按钮时执行。 若要实现自定义操作，从派生类`CMFCEditBrowseCtrl`类，然后重写其[OnBrowse](#onbrowse)方法。  
  
 如果`bEnable`参数是`TRUE`，该控件的浏览模式是`BrowseMode_Default`; 否则为浏览模式是`BrowseMode_None`。 有关浏览模式的详细信息，请参阅[GetMode](#getmode)方法。  
  
##  <a name="a-nameenablefilebrowsebuttona--cmfceditbrowsectrlenablefilebrowsebutton"></a><a name="enablefilebrowsebutton"></a>CMFCEditBrowseCtrl::EnableFileBrowseButton  
 在当前的编辑浏览控件中显示浏览按钮并将控件放入*文件浏览*模式。  
  
```  
void EnableFileBrowseButton(
    LPCTSTR lpszDefExt=NULL,  
    LPCTSTR lpszFilter=NULL,  
    DWORD dwFlags = OFN_HIDEREADONLY | OFN_OVERWRITEPROMPT);
```  
  
### <a name="parameters"></a>参数  
 `lpszDefExt`  
 指定在文件选择对话框中使用的默认文件扩展名。 默认值为 `NULL`。  
  
 `lpszFilter`  
 指定在文件选择对话框中使用的默认筛选器字符串。 默认值为 `NULL`。  
  
 `dwFlags`  
 对话框标志。 默认值是 OFN_HIDEREADONLY 和 OFN_OVERWRITEPROMPT 的按位组合 (OR)。  
  
### <a name="remarks"></a>备注  
 当编辑浏览控件处于文件浏览模式，并且在用户单击浏览按钮时，该控件将显示标准文件选择对话框。  
  
 有关可用标志的完整列表，请参阅[OPENFILENAME 结构](https://msdn.microsoft.com/library/ms646839.aspx)。  
  
##  <a name="a-nameenablefolderbrowsebuttona--cmfceditbrowsectrlenablefolderbrowsebutton"></a><a name="enablefolderbrowsebutton"></a>CMFCEditBrowseCtrl::EnableFolderBrowseButton  
 在当前的编辑浏览控件中显示浏览按钮并将控件放入*文件夹浏览*模式。  
  
```  
void EnableFolderBrowseButton();
```  
  
### <a name="remarks"></a>备注  
 当编辑浏览控件在文件夹浏览模式中并且用户单击浏览按钮时，该控件将显示标准文件夹选择对话框。  
  
##  <a name="a-namegetmodea--cmfceditbrowsectrlgetmode"></a><a name="getmode"></a>CMFCEditBrowseCtrl::GetMode  
 检索当前的编辑浏览控件的浏览模式。  
  
```  
CMFCEditBrowseCtrl::BrowseMode GetMode() const;  
```  
  
### <a name="return-value"></a>返回值  
 指定当前的编辑模式的枚举值之一浏览控件。 浏览模式将确定是否框架显示浏览按钮，当用户单击该按钮时采取的操作。  
  
 下表列出可能的返回值。  
  
|值|说明|  
|-----------|-----------------|  
|`BrowseMode_Default`|`custom mode`。 不执行程序员定义的操作。|  
|`BrowseMode_File`|`file mode`。 显示标准文件浏览器对话框。|  
|`BrowseMode_Folder`|`folder mode`。 显示标准文件夹浏览器对话框。|  
|`BrowseMode_None`|不显示浏览按钮。|  
  
### <a name="remarks"></a>备注  
 默认情况下，`CMFCEditBrowseCtrl`对象初始化为`BrowseMode_None`模式。 修改使用浏览模式[CMFCEditBrowseCtrl::EnableBrowseButton](#enablebrowsebutton)， [CMFCEditBrowseCtrl::EnableFileBrowseButton](#enablefilebrowsebutton)，和[CMFCEditBrowseCtrl::EnableFolderBrowseButton](#enablefolderbrowsebutton)方法。  
  
##  <a name="a-nameonafterupdatea--cmfceditbrowsectrlonafterupdate"></a><a name="onafterupdate"></a>CMFCEditBrowseCtrl::OnAfterUpdate  
 编辑浏览控件更新用的浏览操作的结果后，由框架调用。  
  
```  
virtual void OnAfterUpdate();
```  
  
### <a name="remarks"></a>备注  
 重写此方法在派生类来实现自定义操作。  
  
##  <a name="a-nameonbrowsea--cmfceditbrowsectrlonbrowse"></a><a name="onbrowse"></a>CMFCEditBrowseCtrl::OnBrowse  
 在用户单击编辑浏览控件的浏览按钮之后，由框架调用。  
  
```  
virtual void OnBrowse();
```  
  
### <a name="remarks"></a>备注  
 使用此方法以执行自定义代码，当用户单击编辑浏览控件的浏览按钮。 派生您自己的类从`CMFCEditBrowseCtrl`类并重写其`OnBrowse`方法。 在该方法中，实现自定义浏览操作，并 （可选） 更新编辑浏览控件的文本框。 在您的应用程序，使用[EnableBrowseButton](#enablebrowsebutton)方法，以将编辑浏览控件放入*自定义浏览*模式。  
  
##  <a name="a-nameonchangelayouta--cmfceditbrowsectrlonchangelayout"></a><a name="onchangelayout"></a>CMFCEditBrowseCtrl::OnChangeLayout  
 重绘当前编辑浏览控件。  
  
```  
virtual void OnChangeLayout();
```  
  
### <a name="remarks"></a>备注  
 在浏览模式的编辑浏览控件发生更改时，框架将调用此方法。 有关详细信息，请参阅[CMFCEditBrowseCtrl::GetMode](#getmode)。  
  
##  <a name="a-nameondrawbrowsebuttona--cmfceditbrowsectrlondrawbrowsebutton"></a><a name="ondrawbrowsebutton"></a>CMFCEditBrowseCtrl::OnDrawBrowseButton  
 由框架用于绘制编辑浏览控件上的浏览按钮调用。  
  
```  
virtual void OnDrawBrowseButton(
    CDC* pDC,  
    CRect rect,  
    BOOL bIsButtonPressed,  
    BOOL bIsButtonHot);
```  
  
### <a name="parameters"></a>参数  
 `pDC`  
 一个指向设备上下文的指针。  
  
 `Rect`  
 浏览按钮的边框。  
  
 `bIsButtonPressed`  
 `TRUE`如果按下了按钮;否则为`FALSE`。  
  
 `bIsButtonHot`  
 `TRUE`如果该按钮将突出显示;，否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 重写此函数在派生类自定义浏览按钮的外观。  
  
##  <a name="a-namesetbrowsebuttonimagea--cmfceditbrowsectrlsetbrowsebuttonimage"></a><a name="setbrowsebuttonimage"></a>CMFCEditBrowseCtrl::SetBrowseButtonImage  
 在浏览按钮编辑浏览控件上设置自定义映像。  
  
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
 `hIcon`  
 图标的句柄。  
  
 `hBitmap`  
 位图的句柄。  
  
 `uiBmpResId`  
 一个位图资源 ID。  
  
 `bAutoDestroy`  
 `TRUE`当此方法退出; 中删除指定的图标或位图否则为`FALSE`。 默认值为 `TRUE`。  
  
### <a name="remarks"></a>备注  
 此方法用于将自定义映像应用到浏览按钮。 默认情况下，该框架时，获取标准映像编辑浏览控件是否处于*文件浏览*或*文件夹浏览*模式。  
  
##  <a name="a-nameonillegalfilenamea--cmfceditbrowsectrlonillegalfilename"></a><a name="onillegalfilename"></a>CMFCEditBrowseCtrl::OnIllegalFileName  
 在编辑控件中输入了非法的文件名称时，由框架调用。  
  
```  
virtual BOOL OnIllegalFileName(CString& strFileName);
```  
  
### <a name="parameters"></a>参数  
 `strFileName`  
 指定非法的文件名。  
  
### <a name="return-value"></a>返回值  
 应返回`FALSE`如果进一步文件对话框，可以通过此文件名。 在这种情况下，焦点返回设置到编辑控件和用户应继续编辑。 显示有关非法文件名告知用户一个消息框的默认实现，并返回`FALSE`。 你可以重写此方法，更正文件名，并返回`TRUE`进行进一步处理。  
  
### <a name="remarks"></a>备注  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)

