---
title: "CFindReplaceDialog 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CFindReplaceDialog
- AFXDLGS/CFindReplaceDialog
- AFXDLGS/CFindReplaceDialog::CFindReplaceDialog
- AFXDLGS/CFindReplaceDialog::Create
- AFXDLGS/CFindReplaceDialog::FindNext
- AFXDLGS/CFindReplaceDialog::GetFindString
- AFXDLGS/CFindReplaceDialog::GetNotifier
- AFXDLGS/CFindReplaceDialog::GetReplaceString
- AFXDLGS/CFindReplaceDialog::IsTerminating
- AFXDLGS/CFindReplaceDialog::MatchCase
- AFXDLGS/CFindReplaceDialog::MatchWholeWord
- AFXDLGS/CFindReplaceDialog::ReplaceAll
- AFXDLGS/CFindReplaceDialog::ReplaceCurrent
- AFXDLGS/CFindReplaceDialog::SearchDown
- AFXDLGS/CFindReplaceDialog::m_fr
dev_langs:
- C++
helpviewer_keywords:
- text searches, replacing text
- text searches, CFindReplaceDialog class
- Find/Replace dialog box
- replacing text, CFindReplaceDialog class
- CFindReplaceDialog class
- replacing text
ms.assetid: 610f0b5d-b398-4ef6-8c05-e9d6641e50a8
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
ms.openlocfilehash: 510f6a763dbacb7d4e1b14ea808a4baaaf3d6bf3
ms.lasthandoff: 02/24/2017

---
# <a name="cfindreplacedialog-class"></a>CFindReplaceDialog 类
允许您在您的应用程序中实现标准字符串查找/替换对话框。  
  
## <a name="syntax"></a>语法  
  
```  
class CFindReplaceDialog : public CCommonDialog  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CFindReplaceDialog::CFindReplaceDialog](#cfindreplacedialog)|调用此函数来构造`CFindReplaceDialog`对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CFindReplaceDialog::Create](#create)|创建并显示`CFindReplaceDialog`对话框。|  
|[CFindReplaceDialog::FindNext](#findnext)|调用此函数可确定用户想要查找查找字符串的下一个匹配项。|  
|[CFindReplaceDialog::GetFindString](#getfindstring)|调用此函数可检索当前的查找字符串。|  
|[CFindReplaceDialog::GetNotifier](#getnotifier)|调用此函数可检索**FINDREPLACE**已注册的消息处理程序中的结构。|  
|[CFindReplaceDialog::GetReplaceString](#getreplacestring)|调用此函数可检索当前的替换字符串。|  
|[CFindReplaceDialog::IsTerminating](#isterminating)|调用此函数可确定是否正在终止对话框。|  
|[CFindReplaceDialog::MatchCase](#matchcase)|调用此函数可确定用户想要完全匹配查找字符串的大小写。|  
|[CFindReplaceDialog::MatchWholeWord](#matchwholeword)|调用此函数可确定用户是否希望与整个的单词匹配。|  
|[CFindReplaceDialog::ReplaceAll](#replaceall)|调用此函数可确定用户是否要替换的字符串的所有匹配项。|  
|[CFindReplaceDialog::ReplaceCurrent](#replacecurrent)|调用此函数可确定用户是否要替换当前单词。|  
|[CFindReplaceDialog::SearchDown](#searchdown)|调用此函数可确定用户是否希望继续向下搜索。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CFindReplaceDialog::m_fr](#m_fr)|用于自定义的结构`CFindReplaceDialog`对象。|  
  
## <a name="remarks"></a>备注  
 与其他 Windows 公共对话框，不同`CFindReplaceDialog`对象是无模式时，允许用户在屏幕上处于与其他 windows 进行交互。 有两种类型的`CFindReplaceDialog`对象︰ 查找对话框和查找/替换对话框。 尽管对话框允许用户输入的搜索和搜索/替换字符串，但它们不会执行的任何搜索或替换函数。 您必须添加到应用程序。  
  
 若要构造`CFindReplaceDialog`对象，请使用提供的构造函数 （它不具有任何参数）。 由于这是无模式对话框中，在上分配对象堆使用**新**运算符，而不是在堆栈上。  
  
 一次`CFindReplaceDialog`构造对象，则必须调用[创建](#create)成员函数来创建和显示的对话框。  
  
 使用[m_fr](#m_fr)结构来初始化对话框之前调用**创建**。 `m_fr`结构属于类型[FINDREPLACE](http://msdn.microsoft.com/library/windows/desktop/ms646835)。 此结构的详细信息，请参阅[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 为了使父窗口以查找/替换请求的通知，必须使用 Windows [RegisterWindowMessage](http://msdn.microsoft.com/library/windows/desktop/ms644947)函数，并使用[ON_REGISTERED_MESSAGE](http://msdn.microsoft.com/library/93c1c068-ae8c-4e04-8a60-a603800ab57d)您处理此已注册的消息的框架窗口中的消息映射宏。  
  
 您可以确定用户是否已决定要终止与对话框中`IsTerminating`成员函数。  
  
 `CFindReplaceDialog`依赖于 COMMDLG。随 Windows 3.1 及更高版本一起提供的 DLL 文件。  
  
 要自定义对话框中，从派生类`CFindReplaceDialog`，提供自定义对话框模板上，并添加一个消息映射来处理来自扩展控件的通知消息。 任何未处理的消息应传递给类的基类。  
  
 不需要自定义挂钩函数。  
  
 有关详细信息使用`CFindReplaceDialog`，请参阅[通用对话框类](../../mfc/common-dialog-classes.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 `CFindReplaceDialog`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxdlgs.h  
  
##  <a name="cfindreplacedialog"></a>CFindReplaceDialog::CFindReplaceDialog  
 构造 `CFindReplaceDialog` 对象。  
  
```  
CFindReplaceDialog();
```  
  
### <a name="remarks"></a>备注  
 因为`CFindReplaceDialog`对象是无模式对话框中，必须通过使用构造它在堆上`new`运算符。  
  
 在销毁，框架会尝试执行`delete this`上指向对话框中的指针。 如果在堆栈中，创建对话框中`this`指针不存在而可能会导致未定义的行为。  
  
 有关详细信息的构造`CFindReplaceDialog`对象，请参阅[CFindReplaceDialog](../../mfc/reference/cfindreplacedialog-class.md)概述。 使用[CFindReplaceDialog::Create](#create)成员函数以显示该对话框。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView #&170;](../../mfc/codesnippet/cpp/cfindreplacedialog-class_1.cpp)]  
  
##  <a name="create"></a>CFindReplaceDialog::Create  
 创建并显示查找或查找/替换对话框对象，具体取决于值`bFindDialogOnly`。  
  
```  
virtual BOOL Create(
    BOOL bFindDialogOnly,  
    LPCTSTR lpszFindWhat,  
    LPCTSTR lpszReplaceWith = NULL,  
    DWORD dwFlags = FR_DOWN,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>参数  
 `bFindDialogOnly`  
 此参数设置为`TRUE`显示**查找**对话框。 将其设置为`FALSE`显示**查找/替换**对话框。  
  
 `lpszFindWhat`  
 指向对话框中出现时的默认搜索字符串的指针。 如果`NULL`，对话框中不包含默认搜索字符串。  
  
 `lpszReplaceWith`  
 默认值替换字符串对话框中出现时指针。 如果`NULL`，对话框中不包含默认值替换字符串。  
  
 `dwFlags`  
 可以使用自定义设置对话框中，使用按位 OR 运算符组合在一起的一个或多个标志。 默认值是`FR_DOWN`，它指定是否继续向下搜索。 请参阅[FINDREPLACE](http://msdn.microsoft.com/library/windows/desktop/ms646835)结构中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]有关这些标志的详细信息。  
  
 `pParentWnd`  
 指向对话框中的父窗口或所有者窗口的指针。 这是将收到特别消息，该值指示查找/替换操作请求的窗口。 如果`NULL`，使用该应用程序的主窗口。  
  
### <a name="return-value"></a>返回值  
 已成功创建对话框对象; 如果非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 为了使父窗口以查找/替换请求的通知，必须使用 Windows [RegisterWindowMessage](http://msdn.microsoft.com/library/windows/desktop/ms644947)函数的返回值是唯一的应用程序的实例的消息号。 框架窗口应具有一个声明回调函数的消息映射条目 (`OnFindReplace`在下面的示例中)，来处理此已注册的消息。 下面的代码段演示了如何执行此操作名为的框架窗口类`CMyRichEditView`:  
  
 [!code-cpp[NVC_MFCDocView #&171;](../../mfc/codesnippet/cpp/cfindreplacedialog-class_2.h)]  
  
 [!code-cpp[NVC_MFCDocView #&172;](../../mfc/codesnippet/cpp/cfindreplacedialog-class_3.cpp)]  
  
 [!code-cpp[NVC_MFCDocView #&173;](../../mfc/codesnippet/cpp/cfindreplacedialog-class_4.cpp)]  
  
 在您`OnFindReplace`函数，通过使用解释的用户的意图[CFindReplaceDialog::FindNext](#findnext)和[CFindReplaceDialog::IsTerminating](#isterminating)方法和您创建的查找/替换操作的代码。  
  
### <a name="example"></a>示例  
  请参阅示例[CFindReplaceDialog::CFindReplaceDialog](#cfindreplacedialog)。  
  
##  <a name="findnext"></a>CFindReplaceDialog::FindNext  
 调用此函数从回调函数来确定用户是否希望查找搜索字符串的下一个匹配项。  
  
```  
BOOL FindNext() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果用户想要查找的搜索字符串; 的下一个匹配项，则为非否则为 0。  
  
##  <a name="getfindstring"></a>CFindReplaceDialog::GetFindString  
 调用此函数从您的回调函数以检索要查找的默认字符串。  
  
```  
CString GetFindString() const;  
```  
  
### <a name="return-value"></a>返回值  
 要查找的默认字符串。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView #&69;](../../mfc/codesnippet/cpp/cfindreplacedialog-class_5.cpp)]  
  
##  <a name="getnotifier"></a>CFindReplaceDialog::GetNotifier  
 调用此函数可检索到当前查找替换对话框中的指针。  
  
```  
static CFindReplaceDialog* PASCAL GetNotifier(LPARAM lParam);
```  
  
### <a name="parameters"></a>参数  
 `lParam`  
 **Lparam**值传递到框架窗口的**OnFindReplace**成员函数。  
  
### <a name="return-value"></a>返回值  
 指向当前对话框中的指针。  
  
### <a name="remarks"></a>备注  
 它应该用于在回调函数内访问当前对话框中，调用其成员函数和访问`m_fr`结构。  
  
### <a name="example"></a>示例  
 请参阅[CFindReplaceDialog::Create](#create)以举例说明如何注册要从查找替换对话框中接收通知的 OnFindReplace 处理程序。  
  
 [!code-cpp[NVC_MFCDocView #&69;](../../mfc/codesnippet/cpp/cfindreplacedialog-class_5.cpp)]  
  
##  <a name="getreplacestring"></a>CFindReplaceDialog::GetReplaceString  
 调用此函数可检索当前的替换字符串。  
  
```  
CString GetReplaceString() const;  
```  
  
### <a name="return-value"></a>返回值  
 用来替换找到的字符串默认字符串。  
  
### <a name="example"></a>示例  
  请参阅示例[CFindReplaceDialog::GetFindString](#getfindstring)。  
  
##  <a name="isterminating"></a>CFindReplaceDialog::IsTerminating  
 调用此函数在回调函数来确定用户是否已决定终止对话框。  
  
```  
BOOL IsTerminating() const;  
```  
  
### <a name="return-value"></a>返回值  
 非零，如果用户已决定终止对话框;否则为 0。  
  
### <a name="remarks"></a>备注  
 如果此函数将返回非零，则应调用`DestroyWindow`当前的对话框和任何对话框中为指针变量的组的成员函数**NULL**。 （可选） 您可以将最后一次输入查找/替换文本存储和使用它来初始化下一步查找/替换对话框。  
  
### <a name="example"></a>示例  
  请参阅示例[CFindReplaceDialog::GetFindString](#getfindstring)。  
  
##  <a name="m_fr"></a>CFindReplaceDialog::m_fr  
 用于自定义`CFindReplaceDialog`对象。  
  
```  
FINDREPLACE m_fr;  
```  
  
### <a name="remarks"></a>备注  
 `m_fr`是一种结构类型的[FINDREPLACE](http://msdn.microsoft.com/library/windows/desktop/ms646835)。 其成员存储对话框中对象的特征。 在构造之后`CFindReplaceDialog`对象，可以使用`m_fr`修改对话框中的各个值。  
  
 此结构的详细信息，请参阅**FINDREPLACE**结构中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
  请参阅示例[CFindReplaceDialog::CFindReplaceDialog](#cfindreplacedialog)。  
  
##  <a name="matchcase"></a>CFindReplaceDialog::MatchCase  
 调用此函数可确定用户想要完全匹配查找字符串的大小写。  
  
```  
BOOL MatchCase() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果用户想要查找精确匹配搜索字符串; 的大小写的搜索字符串匹配项，则为非否则为 0。  
  
##  <a name="matchwholeword"></a>CFindReplaceDialog::MatchWholeWord  
 调用此函数可确定用户是否希望与整个的单词匹配。  
  
```  
BOOL MatchWholeWord() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果用户想要匹配的搜索字符串; 仅完整的单词，非零值否则为 0。  
  
##  <a name="replaceall"></a>CFindReplaceDialog::ReplaceAll  
 调用此函数可确定用户是否要替换的字符串的所有匹配项。  
  
```  
BOOL ReplaceAll() const;  
```  
  
### <a name="return-value"></a>返回值  
 非零，如果用户已请求，将替换所有匹配的替换字符串的字符串;否则为 0。  
  
##  <a name="replacecurrent"></a>CFindReplaceDialog::ReplaceCurrent  
 调用此函数可确定用户是否要替换当前单词。  
  
```  
BOOL ReplaceCurrent() const;  
```  
  
### <a name="return-value"></a>返回值  
 非零，如果用户已请求的当前所选的字符串替换的替换字符串;否则为 0。  
  
##  <a name="searchdown"></a>CFindReplaceDialog::SearchDown  
 调用此函数可确定用户是否希望继续向下搜索。  
  
```  
BOOL SearchDown() const;  
```  
  
### <a name="return-value"></a>返回值  
 非零，如果用户想执行搜索，以继续向下方向;如果用户想继续向上搜索为 0。  
  
## <a name="see-also"></a>另请参阅  
 [CCommonDialog 类](../../mfc/reference/ccommondialog-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)  

