---
title: "CFindReplaceDialog 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: d2d39abf526a58b8442107b5ee816f316ae841f5
ms.openlocfilehash: 6ec814e3e96addfdadaaaa855260c8dbd495537e
ms.contentlocale: zh-cn
ms.lasthandoff: 03/31/2017

---
# <a name="cfindreplacedialog-class"></a>CFindReplaceDialog 类
可以在你的应用程序中实现的标准字符串查找/替换对话框。  
  
## <a name="syntax"></a>语法  
  
```  
class CFindReplaceDialog : public CCommonDialog  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CFindReplaceDialog::CFindReplaceDialog](#cfindreplacedialog)|调用此函数可构造`CFindReplaceDialog`对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CFindReplaceDialog::Create](#create)|创建并显示`CFindReplaceDialog`对话框。|  
|[CFindReplaceDialog::FindNext](#findnext)|调用此函数可确定用户是否想要查找的查找字符串的下一个匹配项。|  
|[CFindReplaceDialog::GetFindString](#getfindstring)|调用此函数可检索当前的查找字符串。|  
|[CFindReplaceDialog::GetNotifier](#getnotifier)|调用此函数可检索**FINDREPLACE**已注册的消息处理程序中的结构。|  
|[CFindReplaceDialog::GetReplaceString](#getreplacestring)|调用此函数可检索当前的替换字符串。|  
|[CFindReplaceDialog::IsTerminating](#isterminating)|调用此函数可确定是否正在终止对话框。|  
|[CFindReplaceDialog::MatchCase](#matchcase)|调用此函数可确定用户是否想要完全匹配查找字符串的大小写。|  
|[CFindReplaceDialog::MatchWholeWord](#matchwholeword)|调用此函数可确定用户是否希望匹配完整的字词。|  
|[CFindReplaceDialog::ReplaceAll](#replaceall)|调用此函数可确定用户是否想要替换的字符串的所有匹配项。|  
|[CFindReplaceDialog::ReplaceCurrent](#replacecurrent)|调用此函数可确定用户是否想要替换当前单词。|  
|[CFindReplaceDialog::SearchDown](#searchdown)|调用此函数可确定用户是否希望继续向下搜索。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[CFindReplaceDialog::m_fr](#m_fr)|用于自定义的结构`CFindReplaceDialog`对象。|  
  
## <a name="remarks"></a>备注  
 与其他 Windows 通用对话框，不同`CFindReplaceDialog`对象是无模式，允许用户与其他 windows 交互，当它们在屏幕上时。 有两种类型的`CFindReplaceDialog`对象︰ 查找对话框和查找/替换对话框。 尽管对话框允许用户输入的搜索和搜索/替换字符串，但它们不执行任何搜索或替换函数。 你必须将它们添加到应用程序。  
  
 若要构造`CFindReplaceDialog`对象，请使用提供的构造函数 （其没有自变量）。 由于这是无模式对话框中，分配的对象上堆使用**新**运算符，而不是堆栈上。  
  
 一次`CFindReplaceDialog`构造对象，则必须调用[创建](#create)成员函数来创建和显示对话框。  
  
 使用[m_fr](#m_fr)结构初始化对话框之前调用**创建**。 `m_fr`结构属于类型[FINDREPLACE](http://msdn.microsoft.com/library/windows/desktop/ms646835)。 此结构的详细信息，请参阅[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 在父窗口查找/替换请求的通知的顺序，你必须使用 Windows [RegisterWindowMessage](http://msdn.microsoft.com/library/windows/desktop/ms644947)函数，并使用[ON_REGISTERED_MESSAGE](message-map-macros-mfc.md#on_registered_message)您处理此已注册的消息的框架窗口中的消息映射宏。  
  
 你可以确定用户是否具有决定终止与对话框`IsTerminating`成员函数。  
  
 `CFindReplaceDialog`依赖于 COMMDLG。随 Windows 版本 3.1 和更高版本一起提供的 DLL 文件。  
  
 要自定义对话框中，从派生类`CFindReplaceDialog`，提供自定义对话框模板，并添加一个消息映射来处理来自扩展控件的通知消息。 任何未处理的消息应传递给类的基类。  
  
 自定义挂钩函数不是必需的。  
  
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
 因为`CFindReplaceDialog`对象是一个无模式对话框，你必须通过将它构造堆上`new`运算符。  
  
 在析构，过程 framework 尝试执行`delete this`上指向对话框中的指针。 如果在堆栈中，创建对话框中`this`指针不存在和未定义的行为可能会导致。  
  
 有关详细信息的构造`CFindReplaceDialog`对象，请参阅[CFindReplaceDialog](../../mfc/reference/cfindreplacedialog-class.md)概述。 使用[CFindReplaceDialog::Create](#create)成员函数来显示对话框。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView # 170](../../mfc/codesnippet/cpp/cfindreplacedialog-class_1.cpp)]  
  
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
 将此参数设置为`TRUE`以显示**查找**对话框。 将其设置为`FALSE`以显示**查找/替换**对话框。  
  
 `lpszFindWhat`  
 指向对话框出现时的默认搜索字符串的指针。 如果`NULL`，对话框中不包含默认搜索字符串。  
  
 `lpszReplaceWith`  
 指向对话框出现时的默认替换字符串的指针。 如果`NULL`，对话框中不包含默认替换字符串。  
  
 `dwFlags`  
 可以使用自定义设置对话框中，使用按位 OR 运算符组合在一起的一个或多个标志。 默认值是`FR_DOWN`，它指定是否以继续向下搜索。 请参阅[FINDREPLACE](http://msdn.microsoft.com/library/windows/desktop/ms646835)结构[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]有关这些标志的详细信息。  
  
 `pParentWnd`  
 指向对话框的父或所有者窗口的指针。 这是将收到特别消息，该值指示查找/替换操作请求的窗口。 如果`NULL`，使用应用程序的主窗口。  
  
### <a name="return-value"></a>返回值  
 已成功创建对话框对象; 如果非零否则为 0。  
  
### <a name="remarks"></a>备注  
 在父窗口查找/替换请求的通知的顺序，你必须使用 Windows [RegisterWindowMessage](http://msdn.microsoft.com/library/windows/desktop/ms644947)函数其返回值是唯一的应用程序的实例消息号。 您的框架窗口应具有一个声明回调函数的消息映射条目 (`OnFindReplace`在下面的示例中) 用于处理此已注册的消息。 下面的代码段演示了如何执行此操作的名为的框架窗口类`CMyRichEditView`:  
  
 [!code-cpp[NVC_MFCDocView # 171](../../mfc/codesnippet/cpp/cfindreplacedialog-class_2.h)]  
  
 [!code-cpp[NVC_MFCDocView # 172](../../mfc/codesnippet/cpp/cfindreplacedialog-class_3.cpp)]  
  
 [!code-cpp[NVC_MFCDocView # 173](../../mfc/codesnippet/cpp/cfindreplacedialog-class_4.cpp)]  
  
 在你`OnFindReplace`函数，通过使用解释的用户的意图[CFindReplaceDialog::FindNext](#findnext)和[CFindReplaceDialog::IsTerminating](#isterminating)方法和你创建的查找/替换操作的代码。  
  
### <a name="example"></a>示例  
  请参阅示例[CFindReplaceDialog::CFindReplaceDialog](#cfindreplacedialog)。  
  
##  <a name="findnext"></a>CFindReplaceDialog::FindNext  
 调用此函数从你的回调函数，以确定用户是否想要查找的搜索字符串的下一个匹配项。  
  
```  
BOOL FindNext() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果用户想要查找下一个匹配的搜索字符串中; 则为非 0否则为 0。  
  
##  <a name="getfindstring"></a>CFindReplaceDialog::GetFindString  
 调用此函数从您的回调函数以检索要查找的默认字符串。  
  
```  
CString GetFindString() const;  
```  
  
### <a name="return-value"></a>返回值  
 要查找的默认字符串。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView # 69](../../mfc/codesnippet/cpp/cfindreplacedialog-class_5.cpp)]  
  
##  <a name="getnotifier"></a>CFindReplaceDialog::GetNotifier  
 调用此函数可检索指向当前查找替换对话框中的指针。  
  
```  
static CFindReplaceDialog* PASCAL GetNotifier(LPARAM lParam);
```  
  
### <a name="parameters"></a>参数  
 `lParam`  
 **Lparam**值传递到框架窗口的**OnFindReplace**成员函数。  
  
### <a name="return-value"></a>返回值  
 指向当前的对话框中的指针。  
  
### <a name="remarks"></a>备注  
 它应该用于在回调函数中访问当前对话框中，调用其成员函数和访问`m_fr`结构。  
  
### <a name="example"></a>示例  
 请参阅[CFindReplaceDialog::Create](#create)有关如何注册 OnFindReplace 处理程序来从查找替换对话框中接收通知的示例。  
  
 [!code-cpp[NVC_MFCDocView # 69](../../mfc/codesnippet/cpp/cfindreplacedialog-class_5.cpp)]  
  
##  <a name="getreplacestring"></a>CFindReplaceDialog::GetReplaceString  
 调用此函数可检索当前的替换字符串。  
  
```  
CString GetReplaceString() const;  
```  
  
### <a name="return-value"></a>返回值  
 用于替换找到的字符串默认字符串。  
  
### <a name="example"></a>示例  
  请参阅示例[CFindReplaceDialog::GetFindString](#getfindstring)。  
  
##  <a name="isterminating"></a>CFindReplaceDialog::IsTerminating  
 调用此函数在你的回调函数，以确定用户是否具有决定终止对话框。  
  
```  
BOOL IsTerminating() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果用户决定终止对话框; 则为非 0否则为 0。  
  
### <a name="remarks"></a>备注  
 如果此函数返回非零，则应调用`DestroyWindow`的当前的对话框和任何对话框指针变量的组的成员函数**NULL**。 或者，你还可以存储上一次输入的查找/替换文本并使用它来初始化下一步查找/替换对话框。  
  
### <a name="example"></a>示例  
  请参阅示例[CFindReplaceDialog::GetFindString](#getfindstring)。  
  
##  <a name="m_fr"></a>CFindReplaceDialog::m_fr  
 用于自定义`CFindReplaceDialog`对象。  
  
```  
FINDREPLACE m_fr;  
```  
  
### <a name="remarks"></a>备注  
 `m_fr`是一种类型的结构[FINDREPLACE](http://msdn.microsoft.com/library/windows/desktop/ms646835)。 其成员存储对话框对象的特征。 后构造`CFindReplaceDialog`对象时，可以使用`m_fr`修改在对话框中的各种值。  
  
 此结构的详细信息，请参阅**FINDREPLACE**结构[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
  请参阅示例[CFindReplaceDialog::CFindReplaceDialog](#cfindreplacedialog)。  
  
##  <a name="matchcase"></a>CFindReplaceDialog::MatchCase  
 调用此函数可确定用户是否想要完全匹配查找字符串的大小写。  
  
```  
BOOL MatchCase() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果用户想要查找完全匹配的搜索字符串; 的大小写的搜索字符串匹配项则不为否则为 0。  
  
##  <a name="matchwholeword"></a>CFindReplaceDialog::MatchWholeWord  
 调用此函数可确定用户是否希望匹配完整的字词。  
  
```  
BOOL MatchWholeWord() const;  
```  
  
### <a name="return-value"></a>返回值  
 非零，如果用户想要匹配的搜索字符串; 仅完整的字词否则为 0。  
  
##  <a name="replaceall"></a>CFindReplaceDialog::ReplaceAll  
 调用此函数可确定用户是否想要替换的字符串的所有匹配项。  
  
```  
BOOL ReplaceAll() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果用户已请求，将替换所有匹配的替换字符串的字符串; 则为非 0否则为 0。  
  
##  <a name="replacecurrent"></a>CFindReplaceDialog::ReplaceCurrent  
 调用此函数可确定用户是否想要替换当前单词。  
  
```  
BOOL ReplaceCurrent() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果用户已请求的当前所选的字符串替换的替换字符串; 则为非 0否则为 0。  
  
##  <a name="searchdown"></a>CFindReplaceDialog::SearchDown  
 调用此函数可确定用户是否希望继续向下搜索。  
  
```  
BOOL SearchDown() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果用户想搜索继续方向向下; 则为非 0如果用户想继续向上搜索为 0。  
  
## <a name="see-also"></a>另请参阅  
 [CCommonDialog 类](../../mfc/reference/ccommondialog-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)  

