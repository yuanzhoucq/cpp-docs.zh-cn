---
title: "CEditView 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CEditView
- AFXEXT/CEditView
- AFXEXT/CEditView::CEditView
- AFXEXT/CEditView::FindText
- AFXEXT/CEditView::GetBufferLength
- AFXEXT/CEditView::GetEditCtrl
- AFXEXT/CEditView::GetPrinterFont
- AFXEXT/CEditView::GetSelectedText
- AFXEXT/CEditView::LockBuffer
- AFXEXT/CEditView::PrintInsideRect
- AFXEXT/CEditView::SerializeRaw
- AFXEXT/CEditView::SetPrinterFont
- AFXEXT/CEditView::SetTabStops
- AFXEXT/CEditView::UnlockBuffer
- AFXEXT/CEditView::OnFindNext
- AFXEXT/CEditView::OnReplaceAll
- AFXEXT/CEditView::OnReplaceSel
- AFXEXT/CEditView::OnTextNotFound
- AFXEXT/CEditView::dwStyleDefault
dev_langs: C++
helpviewer_keywords:
- CEditView [MFC], CEditView
- CEditView [MFC], FindText
- CEditView [MFC], GetBufferLength
- CEditView [MFC], GetEditCtrl
- CEditView [MFC], GetPrinterFont
- CEditView [MFC], GetSelectedText
- CEditView [MFC], LockBuffer
- CEditView [MFC], PrintInsideRect
- CEditView [MFC], SerializeRaw
- CEditView [MFC], SetPrinterFont
- CEditView [MFC], SetTabStops
- CEditView [MFC], UnlockBuffer
- CEditView [MFC], OnFindNext
- CEditView [MFC], OnReplaceAll
- CEditView [MFC], OnReplaceSel
- CEditView [MFC], OnTextNotFound
- CEditView [MFC], dwStyleDefault
ms.assetid: bf38255c-fcbe-450c-95b2-3c5e35f86c37
caps.latest.revision: "25"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 38b8389418657499d43263399f1a05b3a0326c84
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="ceditview-class"></a>CEditView 类
视图类的类型，提供 Windows 编辑控件功能并可用于实现简单的文本编辑器功能。  
  
## <a name="syntax"></a>语法  
  
```  
class CEditView : public CCtrlView  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CEditView::CEditView](#ceditview)|构造 `CEditView` 类型的对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CEditView::FindText](#findtext)|搜索文本中的字符串。|  
|[CEditView::GetBufferLength](#getbufferlength)|获取字符缓冲区的长度。|  
|[CEditView::GetEditCtrl](#geteditctrl)|提供对访问`CEdit`部分`CEditView`（Windows 编辑控件） 的对象。|  
|[CEditView::GetPrinterFont](#getprinterfont)|检索当前的打印机字体。|  
|[CEditView::GetSelectedText](#getselectedtext)|检索当前所选文本。|  
|[CEditView::LockBuffer](#lockbuffer)|锁定缓冲区。|  
|[CEditView::PrintInsideRect](#printinsiderect)|呈现给定矩形内的文本。|  
|[CEditView::SerializeRaw](#serializeraw)|序列化`CEditView`为磁盘上原始文本的对象。|  
|[CEditView::SetPrinterFont](#setprinterfont)|设置新的打印机字体。|  
|[CEditView::SetTabStops](#settabstops)|设置制表用于屏幕显示和打印。|  
|[CEditView::UnlockBuffer](#unlockbuffer)|解除锁定缓冲区。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|描述|  
|----------|-----------------|  
|[CEditView::OnFindNext](#onfindnext)|查找下一个匹配项的文本字符串。|  
|[CEditView::OnReplaceAll](#onreplaceall)|使用新的字符串来替换给定字符串的所有匹配项。|  
|[CEditView::OnReplaceSel](#onreplacesel)|将替换当前所选内容。|  
|[CEditView::OnTextNotFound](#ontextnotfound)|查找操作失败以匹配任何进一步的文本时调用。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CEditView::dwStyleDefault](#dwstyledefault)|默认类型的对象的样式**CEditView。**|  
  
## <a name="remarks"></a>备注  
 `CEditView`类提供以下附加功能：  
  
-   打印。  
  
-   查找和替换。  
  
 因为类`CEditView`是类的派生`CView`，类的对象`CEditView`可以用于文档和文档模板。  
  
 每个`CEditView`控件的文本保留在其自己的全局内存对象。 你的应用程序可以有任意数量的`CEditView`对象。  
  
 创建类型的对象`CEditView`如果你想编辑窗口与上面列出的额外功能或如果你希望简单的文本编辑器功能。 A`CEditView`对象可能会处于一个窗口的整个工作区。 派生您自己的类从`CEditView`以添加或修改的基本功能，或声明可以添加到文档模板的类。  
  
 类的默认实现`CEditView`处理以下命令： **ID_EDIT_SELECT_ALL**， **ID_EDIT_FIND**， **ID_EDIT_REPLACE**， **ID_EDIT_REPEAT**，和**ID_FILE_PRINT**。  
  
 默认字符限制`CEditView`是 (1024年\*1024年-1 = 1048575)。 这可以通过调用更改**EM_LIMITTEXT**函数的基础编辑控件。 但是的限制是操作系统而异，并且的一种编辑控件 （单个或多行）。 有关这些限制的详细信息，请参阅[EM_LIMITTEXT](http://msdn.microsoft.com/library/windows/desktop/bb761607)。  
  
 若要更改控件中的此限制，重写`OnCreate()`函数你`CEditView`类并插入以下代码行：  
  
 [!code-cpp[NVC_MFCDocView#65](../../mfc/codesnippet/cpp/ceditview-class_1.cpp)]  
  
 类型的对象`CEditView`(或派生自的类型`CEditView`) 具有以下限制：  
  
- `CEditView`不实现 true 所见即所得 (WYSIWYG) 编辑。 ： 在屏幕上的提高可读性并对匹配的打印的输出之间有一个选择`CEditView`选取屏幕可读性。  
  
- `CEditView`可以在只有一种字体显示文本。 尚无特殊字符格式设置支持。 请参阅类[CRichEditView](../../mfc/reference/cricheditview-class.md)的更强大的功能。  
  
-   文本量`CEditView`可以包含限制。 限制是相同`CEdit`控件。  
  
 有关详细信息`CEditView`，请参阅[派生视图类 MFC 中可用](../../mfc/derived-view-classes-available-in-mfc.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CView](../../mfc/reference/cview-class.md)  
  
 [CCtrlView](../../mfc/reference/cctrlview-class.md)  
  
 `CEditView`  
  
## <a name="requirements"></a>要求  
 **标头：** afxext.h  
  
##  <a name="ceditview"></a>CEditView::CEditView  
 构造 `CEditView` 类型的对象。  
  
```  
CEditView();
```  
  
### <a name="remarks"></a>备注  
 在构造对象之后, 必须调用[cwnd:: Create](../../mfc/reference/cwnd-class.md#create)函数之前使用编辑控件。 如果派生的类从`CEditView`并将其添加到模板使用`CWinApp::AddDocTemplate`，框架会调用这两个此构造函数和**创建**函数。  
  
##  <a name="dwstyledefault"></a>CEditView::dwStyleDefault  
 包含的默认样式`CEditView`对象。  
  
```  
static const DWORD dwStyleDefault;  
```  
  
### <a name="remarks"></a>备注  
 将传递作为此静态成员`dwStyle`参数**创建**函数来获取的默认样式`CEditView`对象。  
  
##  <a name="findtext"></a>CEditView::FindText  
 调用`FindText`函数要搜索`CEditView`对象的文本缓冲区。  
  
```  
BOOL FindText(
    LPCTSTR lpszFind,  
    BOOL bNext = TRUE,  
    BOOL bCase = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `lpszFind`  
 要找的文本。  
  
 `bNext`  
 指定搜索的方向。 如果**TRUE**，搜索方向将是朝向缓冲区末尾。 如果**FALSE**，搜索方向将是朝向缓冲区开头。  
  
 `bCase`  
 指定是否搜索不区分大小写。 如果**TRUE**，搜索不区分大小写。 如果**FALSE**，搜索不区分大小写。  
  
### <a name="return-value"></a>返回值  
 如果找到搜索文本; 则为非 0否则为 0。  
  
### <a name="remarks"></a>备注  
 此函数搜索指定的文本的缓冲区中的文本`lpszFind`中由指定的方向的当前选定处开始， `bNext`，并使用指定的大小写区分功能`bCase`。 如果找到了文本，它将所选内容设置为找到的文本，并返回一个非零值。 如果没有找到文本，该函数将返回 0。  
  
 通常不需要调用`FindText`作用，除非你重写`OnFindNext`，哪些调用`FindText`。  
  
##  <a name="getbufferlength"></a>CEditView::GetBufferLength  
 调用此成员函数可获取当前在编辑控件的缓冲区中，不包括 null 终止符的字符数。  
  
```  
UINT GetBufferLength() const;  
```  
  
### <a name="return-value"></a>返回值  
 缓冲区中的字符串的长度。  
  
##  <a name="geteditctrl"></a>CEditView::GetEditCtrl  
 调用`GetEditCtrl`以获取对使用编辑视图的编辑控件的引用。  
  
```  
CEdit& GetEditCtrl() const;  
```  
  
### <a name="return-value"></a>返回值  
 对 `CEdit` 对象的引用。  
  
### <a name="remarks"></a>备注  
 此控件是类型[CEdit](../../mfc/reference/cedit-class.md)，因此你能够直接使用的 Windows 编辑控件`CEdit`成员函数。  
  
> [!CAUTION]
>  使用`CEdit`对象可以更改基础窗口的状态编辑控件。 例如，不应更改使用的选项卡设置[CEdit::SetTabStops](../../mfc/reference/cedit-class.md#settabstops)正常，因为`CEditView`缓存使用在编辑控件和在打印中的这些设置。 请改用[CEditView::SetTabStops](#settabstops)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#66](../../mfc/codesnippet/cpp/ceditview-class_2.cpp)]  
  
##  <a name="getprinterfont"></a>CEditView::GetPrinterFont  
 调用`GetPrinterFont`以获取指向[CFont](../../mfc/reference/cfont-class.md)对象，描述当前打印机字体。  
  
```  
CFont* GetPrinterFont() const;  
```  
  
### <a name="return-value"></a>返回值  
 指向的指针`CFont`对象，它指定当前的打印机字体;**NULL**如果尚未设置打印机字体。 该指针可能是暂时的，不应存储起来供将来使用。  
  
### <a name="remarks"></a>备注  
 如果打印机字体尚未设置，默认打印行为`CEditView`类为输出使用与用于显示的字体相同。  
  
 使用此函数可确定当前的打印机字体。 如果它不是所需的打印机字体，使用[CEditView::SetPrinterFont](#setprinterfont)若要更改它。  
  
##  <a name="getselectedtext"></a>CEditView::GetSelectedText  
 调用`GetSelectedText`要复制到所选的文本`CString`对象，直至选定内容或选定内容中前面的第一个回车符-字符的字符的末尾。  
  
```  
void GetSelectedText(CString& strResult) const;  
```  
  
### <a name="parameters"></a>参数  
 `strResult`  
 对引用`CString`将接收所选的文本的对象。  
  
##  <a name="lockbuffer"></a>CEditView::LockBuffer  
 调用此成员函数以获取指向缓冲区的指针。 不应修改缓冲区。  
  
```  
LPCTSTR LockBuffer() const;  
```  
  
### <a name="return-value"></a>返回值  
 指向编辑控件的缓冲区的指针。  
  
##  <a name="onfindnext"></a>CEditView::OnFindNext  
 搜索指定的文本的缓冲区中的文本`lpszFind`，沿指定方向`bNext`，与由指定的大小写区分功能`bCase`。  
  
```  
virtual void OnFindNext(
    LPCTSTR lpszFind,  
    BOOL bNext,  
    BOOL bCase);
```  
  
### <a name="parameters"></a>参数  
 `lpszFind`  
 要找的文本。  
  
 `bNext`  
 指定搜索的方向。 如果**TRUE**，搜索方向将是朝向缓冲区末尾。 如果**FALSE**，搜索方向将是朝向缓冲区开头。  
  
 `bCase`  
 指定是否搜索不区分大小写。 如果**TRUE**，搜索不区分大小写。 如果**FALSE**，搜索不区分大小写。  
  
### <a name="remarks"></a>备注  
 搜索当前所选内容的开头开始，并通过调用来实现[FindText](#findtext)。 在默认实现中，`OnFindNext`调用[OnTextNotFound](#ontextnotfound)如果没有找到文本。  
  
 重写`OnFindNext`更改的方式`CEditView`-派生的对象搜索文本。 `CEditView`调用`OnFindNext`当用户选择在标准的查找对话框中的查找下一步按钮。  
  
##  <a name="onreplaceall"></a>CEditView::OnReplaceAll  
 `CEditView`调用`OnReplaceAll`当用户在标准的替换对话框中选择全部替换按钮。  
  
```  
virtual void OnReplaceAll(
    LPCTSTR lpszFind,  
    LPCTSTR lpszReplace,  
    BOOL bCase);
```  
  
### <a name="parameters"></a>参数  
 `lpszFind`  
 要找的文本。  
  
 `lpszReplace`  
 要替换搜索文本的文本。  
  
 `bCase`  
 指定搜索是否区分大小写。 如果**TRUE**，搜索不区分大小写。 如果**FALSE**，搜索不区分大小写。  
  
### <a name="remarks"></a>备注  
 `OnReplaceAll`搜索指定的文本的缓冲区中的文本`lpszFind`，使用指定的大小写区分功能`bCase`。 当前所选内容的开头开始搜索。 每次发现搜索文本时，则此函数会将文本该匹配项替换与指定的文本`lpszReplace`。 搜索通过调用[FindText](#findtext)。 在默认实现中， [OnTextNotFound](#ontextnotfound)如果没有找到文本，则调用。  
  
 如果当前所选内容不匹配`lpszFind`，所选内容更新到指定的文本的第一个匹配项`lpszFind`并且不执行替换操作。 这允许用户为确认这是他们想要选择与要替换的文本不匹配时执行的操作。  
  
 重写`OnReplaceAll`更改的方式`CEditView`-派生的对象替换文本。  
  
##  <a name="onreplacesel"></a>CEditView::OnReplaceSel  
 `CEditView`调用`OnReplaceSel`当用户在标准的替换对话框中选择替换按钮。  
  
```  
virtual void OnReplaceSel(
    LPCTSTR lpszFind,  
    BOOL bNext,  
    BOOL bCase,  
    LPCTSTR lpszReplace);
```  
  
### <a name="parameters"></a>参数  
 `lpszFind`  
 要找的文本。  
  
 `bNext`  
 指定搜索的方向。 如果**TRUE**，搜索方向将是朝向缓冲区末尾。 如果**FALSE**，搜索方向将是朝向缓冲区开头。  
  
 `bCase`  
 指定是否搜索不区分大小写。 如果**TRUE**，搜索不区分大小写。 如果**FALSE**，搜索不区分大小写。  
  
 `lpszReplace`  
 要替换找到的文本的文本。  
  
### <a name="remarks"></a>备注  
 将所选内容后, 此函数搜索的文本中指定的文本的下一个匹配项的缓冲区`lpszFind`，沿指定方向`bNext`，与由指定的区分大小写`bCase`。 搜索通过调用[FindText](#findtext)。 如果没有找到文本， [OnTextNotFound](#ontextnotfound)调用。  
  
 重写`OnReplaceSel`更改的方式`CEditView`-派生的对象将替换所选的文本。  
  
##  <a name="ontextnotfound"></a>CEditView::OnTextNotFound  
 重写此函数可更改的默认实现，后者将调用 Windows 函数**MessageBeep**。  
  
```  
virtual void OnTextNotFound(LPCTSTR lpszFind);
```  
  
### <a name="parameters"></a>参数  
 `lpszFind`  
 要找的文本。  
  
##  <a name="printinsiderect"></a>CEditView::PrintInsideRect  
 调用`PrintInsideRect`若要在由指定的矩形中打印文本*rectLayout*。  
  
```  
UINT PrintInsideRect(
    CDC *pDC,  
    RECT& rectLayout,  
    UINT nIndexStart,  
    UINT nIndexStop);
```  
  
### <a name="parameters"></a>参数  
 `pDC`  
 指向打印机设备上下文的指针。  
  
 *rectLayout*  
 引用[CRect](../../atl-mfc-shared/reference/crect-class.md)对象或[RECT 结构](../../mfc/reference/rect-structure1.md)指定是用要呈现文本的矩形。  
  
 `nIndexStart`  
 索引中要呈现的第一个字符的缓冲区。  
  
 `nIndexStop`  
 索引中要呈现的最后一个字符后面的字符的缓冲区。  
  
### <a name="return-value"></a>返回值  
 要打印的下一个字符的索引 （也就是说，呈现最后一个字符后面的字符）。  
  
### <a name="remarks"></a>备注  
 如果`CEditView`控件不具有样式**ES_AUTOHSCROLL**，文本包装呈现矩形中。 如果控件确实具有样式**ES_AUTOHSCROLL**，文本将被剪裁矩形的右边缘。  
  
 **Rect.bottom**元素*rectLayout*对象已更改，从而使矩形的维度定义原始文本所占用的矩形的部分。  
  
##  <a name="serializeraw"></a>CEditView::SerializeRaw  
 调用`SerializeRaw`能够`CArchive`对象读取或写入文本`CEditView`到文本文件的对象。  
  
```  
void SerializeRaw(CArchive& ar);
```  
  
### <a name="parameters"></a>参数  
 `ar`  
 引用`CArchive`对象，用于存储的序列化的文本。  
  
### <a name="remarks"></a>备注  
 `SerializeRaw`不同于`CEditView`的内部实现`Serialize`在于它读取和写入纯文本，而无需前面对象说明数据。  
  
##  <a name="setprinterfont"></a>CEditView::SetPrinterFont  
 调用`SetPrinterFont`到由指定的字体设置的打印机字体`pFont`。  
  
```  
void SetPrinterFont(CFont* pFont);
```  
  
### <a name="parameters"></a>参数  
 `pFont`  
 指向类型的对象的指针`CFont`。 如果**NULL**，用于打印的字体开始算起的显示字体。  
  
### <a name="remarks"></a>备注  
 如果您希望始终使用特定字体打印你视图，包括调用`SetPrinterFont`在类的`OnPreparePrinting`函数。 此虚函数之前调用打印发生，因此字体更改发生在之前打印视图的内容。  
  
##  <a name="settabstops"></a>CEditView::SetTabStops  
 调用此函数可设置用于显示和打印的制表位。  
  
```  
void SetTabStops(int nTabStops);
```  
  
### <a name="parameters"></a>参数  
 `nTabStops`  
 每个制表位，对话框单位的宽度。  
  
### <a name="remarks"></a>备注  
 支持只是一个单一的制表位宽度。 (`CEdit`对象支持多个选项卡宽度。)宽度是采用对话框单位等于 1 / 4 的平均字符宽度 （基于大写和小写字母字符仅） 在打印或显示时使用的字体。 不应使用`CEdit::SetTabStops`因为`CEditView`必须缓存的制表位值。  
  
 此函数修改仅为其调用的对象的选项卡。 若要更改选项卡停止每个`CEditView`对象在你的应用程序，请调用每个对象的`SetTabStops`函数。  
  
### <a name="example"></a>示例  
 此代码段通过仔细度量该控件使用的字体中对每个第四个字符的控制设置制表位。  
  
 [!code-cpp[NVC_MFCDocView#67](../../mfc/codesnippet/cpp/ceditview-class_3.cpp)]  
  
##  <a name="unlockbuffer"></a>CEditView::UnlockBuffer  
 调用此成员函数以解锁缓冲区。  
  
```  
void UnlockBuffer() const;  
```  
  
### <a name="remarks"></a>备注  
 调用`UnlockBuffer`使用返回的指针完后[LockBuffer](#lockbuffer)。  
  
## <a name="see-also"></a>另请参阅  
 [MFC 示例 SUPERPAD](../../visual-cpp-samples.md)   
 [CCtrlView 类](../../mfc/reference/cctrlview-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CEdit 类](../../mfc/reference/cedit-class.md)   
 [CDocument 类](../../mfc/reference/cdocument-class.md)   
 [CDocTemplate 类](../../mfc/reference/cdoctemplate-class.md)   
 [CCtrlView 类](../../mfc/reference/cctrlview-class.md)   
 [CRichEditView 类](../../mfc/reference/cricheditview-class.md)
