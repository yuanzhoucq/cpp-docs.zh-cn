---
title: "CEditView 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CEditView
dev_langs:
- C++
helpviewer_keywords:
- text editors, CEditView class
- text editors
- edit controls, classes
- views, classes
- CEditView class
ms.assetid: bf38255c-fcbe-450c-95b2-3c5e35f86c37
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
ms.openlocfilehash: 688a6c0e871a9456b85a8ed02ce43d7fa9ca8180
ms.lasthandoff: 02/24/2017

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
|[CEditView::GetSelectedText](#getselectedtext)|检索当前选定文本。|  
|[CEditView::LockBuffer](#lockbuffer)|锁定缓冲区。|  
|[CEditView::PrintInsideRect](#printinsiderect)|将呈现在给定的矩形内的文本。|  
|[CEditView::SerializeRaw](#serializeraw)|将序列化为`CEditView`为磁盘上原始文本的对象。|  
|[CEditView::SetPrinterFont](#setprinterfont)|将新的打印机字体设置。|  
|[CEditView::SetTabStops](#settabstops)|设置制表屏幕显示和打印。|  
|[CEditView::UnlockBuffer](#unlockbuffer)|对缓冲区进行解锁。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|说明|  
|----------|-----------------|  
|[CEditView::OnFindNext](#onfindnext)|查找下一个匹配项的文本字符串。|  
|[CEditView::OnReplaceAll](#onreplaceall)|使用新的字符串来替换给定字符串的所有匹配项。|  
|[CEditView::OnReplaceSel](#onreplacesel)|将替换当前所选内容。|  
|[CEditView::OnTextNotFound](#ontextnotfound)|当查找操作没有找到匹配的任何进一步的文本时调用。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[CEditView::dwStyleDefault](#dwstyledefault)|默认类型的对象的样式**CEditView。**|  
  
## <a name="remarks"></a>备注  
 `CEditView`类提供以下附加功能︰  
  
-   打印。  
  
-   查找和替换。  
  
 因为类`CEditView`由派生类`CView`，类的对象`CEditView`可以用于文档和文档模板。  
  
 每个`CEditView`控件的文本就会保留在其自己的全局内存的对象。 您的应用程序可以有任意数量的`CEditView`对象。  
  
 创建类型的对象`CEditView`如果您希望编辑窗口与以上所列的额外功能或要简单文本编辑器的功能。 一个`CEditView`对象可能会处于窗口的整个客户端区域。 派生您自己的类从`CEditView`添加或修改的基本功能，或声明可以添加到文档模板的类。  
  
 类的默认实现`CEditView`处理以下命令︰ **ID_EDIT_SELECT_ALL**， **ID_EDIT_FIND**， **ID_EDIT_REPLACE**， **ID_EDIT_REPEAT**，和**ID_FILE_PRINT**。  
  
 默认字符限制`CEditView`是 (1024年\*1024年-1 = 1048575)。 这可以通过调用更改**EM_LIMITTEXT** edit 控件中的基础功能。 但是，限制为操作系统而异，并且的一种编辑控件 （一个或多行）。 有关这些限制的详细信息，请参阅[EM_LIMITTEXT](http://msdn.microsoft.com/library/windows/desktop/bb761607)。  
  
 若要更改控件中的此限制，请重写`OnCreate()`函数为您`CEditView`类，并插入以下代码行︰  
  
 [!code-cpp[NVC_MFCDocView #&65;](../../mfc/codesnippet/cpp/ceditview-class_1.cpp)]  
  
 类型的对象`CEditView`(或派生的类型的`CEditView`) 具有以下限制︰  
  
- `CEditView`未实现 true 所见即所得 (WYSIWYG) 编辑。 在屏幕上的可读性和匹配的打印的输出之间没有一个选择`CEditView`选取屏幕可读性。  
  
- `CEditView`可以在仅一种字体显示文本。 尚无特殊字符格式设置支持。 请参见类[CRichEditView](../../mfc/reference/cricheditview-class.md)的更强大的功能。  
  
-   文本量`CEditView`可以包含限制。 限制为相同`CEdit`控件。  
  
 有关详细信息`CEditView`，请参阅[派生视图类在 MFC 中提供](../../mfc/derived-view-classes-available-in-mfc.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CView](../../mfc/reference/cview-class.md)  
  
 [CCtrlView](../../mfc/reference/cctrlview-class.md)  
  
 `CEditView`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxext.h  
  
##  <a name="a-nameceditviewa--ceditviewceditview"></a><a name="ceditview"></a>CEditView::CEditView  
 构造 `CEditView` 类型的对象。  
  
```  
CEditView();
```  
  
### <a name="remarks"></a>备注  
 构造该对象，则必须调用[cwnd:: Create](../../mfc/reference/cwnd-class.md#create)函数之前使用编辑控件。 如果您从派生类`CEditView`并将其添加到模板使用`CWinApp::AddDocTemplate`，框架将调用这两个此构造函数和**创建**函数。  
  
##  <a name="a-namedwstyledefaulta--ceditviewdwstyledefault"></a><a name="dwstyledefault"></a>CEditView::dwStyleDefault  
 包含的默认样式`CEditView`对象。  
  
```  
static const DWORD dwStyleDefault;  
```  
  
### <a name="remarks"></a>备注  
 将传递作为此静态成员`dwStyle`参数**创建**函数来获取的默认样式为`CEditView`对象。  
  
##  <a name="a-namefindtexta--ceditviewfindtext"></a><a name="findtext"></a>CEditView::FindText  
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
 指定搜索方向。 如果**TRUE**，搜索方向将是朝向缓冲区的末尾。 如果**FALSE**，搜索方向将是朝向该缓冲区的开头。  
  
 `bCase`  
 指定该搜索是否区分大小写。 如果**TRUE**，搜索不区分大小写。 如果**FALSE**，搜索不区分大小写。  
  
### <a name="return-value"></a>返回值  
 如果找到搜索文本，则非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 此函数在指定的文本的缓冲区中搜索的文本`lpszFind`中指定的方向的当前选定处开始， `bNext`，并由指定的大小写区分功能与`bCase`。 如果找到了文本，它将所选内容设置为所找到文本，并返回一个非零值。 如果未找到文本，该函数将返回 0。  
  
 通常不需要调用`FindText`函数，除非您重写`OnFindNext`，后者调用`FindText`。  
  
##  <a name="a-namegetbufferlengtha--ceditviewgetbufferlength"></a><a name="getbufferlength"></a>CEditView::GetBufferLength  
 调用该成员函数以获取当前在编辑控件的缓冲区中不包括 null 终止符的字符数。  
  
```  
UINT GetBufferLength() const;  
```  
  
### <a name="return-value"></a>返回值  
 缓冲区中字符串的长度。  
  
##  <a name="a-namegeteditctrla--ceditviewgeteditctrl"></a><a name="geteditctrl"></a>CEditView::GetEditCtrl  
 调用`GetEditCtrl`以获取对使用编辑视图的编辑控件的引用。  
  
```  
CEdit& GetEditCtrl() const;  
```  
  
### <a name="return-value"></a>返回值  
 对 `CEdit` 对象的引用。  
  
### <a name="remarks"></a>备注  
 此控件是类型[CEdit](../../mfc/reference/cedit-class.md)，因此您可以操作 Windows 编辑控件直接使用`CEdit`成员函数。  
  
> [!CAUTION]
>  使用`CEdit`对象可以将更改状态的基础 Windows 编辑控件。 例如，不应更改使用的选项卡上设置[CEdit::SetTabStops](../../mfc/reference/cedit-class.md#settabstops)正常，因为`CEditView`缓存使用编辑控件中，又可以在打印中的这些设置。 请改用[CEditView::SetTabStops](#settabstops)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView #&66;](../../mfc/codesnippet/cpp/ceditview-class_2.cpp)]  
  
##  <a name="a-namegetprinterfonta--ceditviewgetprinterfont"></a><a name="getprinterfont"></a>CEditView::GetPrinterFont  
 调用`GetPrinterFont`以获取指向[CFont](../../mfc/reference/cfont-class.md)对象，用于描述当前打印机字体。  
  
```  
CFont* GetPrinterFont() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个指向`CFont`对象，它指定当前的打印机字体;**NULL**如果尚未设置打印机字体。 该指针可能是暂时的，不应存储起来供将来使用。  
  
### <a name="remarks"></a>备注  
 如果打印机字体尚未设置，默认打印行为`CEditView`类是使用用于显示的相同字体进行打印。  
  
 使用此函数可确定当前的打印机字体。 如果它不是所需的打印机字体，使用[CEditView::SetPrinterFont](#setprinterfont)以更改它。  
  
##  <a name="a-namegetselectedtexta--ceditviewgetselectedtext"></a><a name="getselectedtext"></a>CEditView::GetSelectedText  
 调用`GetSelectedText`要复制到所选的文本`CString`对象，直至选定内容或选定内容中前面的第一个回车符的字符的字符的末尾。  
  
```  
void GetSelectedText(CString& strResult) const;  
```  
  
### <a name="parameters"></a>参数  
 `strResult`  
 对引用`CString`是否要接收选定的文本的对象。  
  
##  <a name="a-namelockbuffera--ceditviewlockbuffer"></a><a name="lockbuffer"></a>CEditView::LockBuffer  
 调用该成员函数以获取指向缓冲区的指针。 不应修改缓冲区。  
  
```  
LPCTSTR LockBuffer() const;  
```  
  
### <a name="return-value"></a>返回值  
 指向编辑控件的缓冲区的指针。  
  
##  <a name="a-nameonfindnexta--ceditviewonfindnext"></a><a name="onfindnext"></a>CEditView::OnFindNext  
 搜索指定的文本的缓冲区中的文本`lpszFind`，在指定的方向`bNext`，与由指定的大小写区分功能`bCase`。  
  
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
 指定搜索方向。 如果**TRUE**，搜索方向将是朝向缓冲区的末尾。 如果**FALSE**，搜索方向将是朝向该缓冲区的开头。  
  
 `bCase`  
 指定该搜索是否区分大小写。 如果**TRUE**，搜索不区分大小写。 如果**FALSE**，搜索不区分大小写。  
  
### <a name="remarks"></a>备注  
 搜索当前所选内容的开头开始，并通过调用来实现[FindText](#findtext)。 在默认实现中，`OnFindNext`调用[OnTextNotFound](#ontextnotfound)如果没有找到文本。  
  
 重写`OnFindNext`更改的方式`CEditView`-派生的对象中搜索文本。 `CEditView`调用`OnFindNext`当用户在标准的查找对话框中选择查找下一个按钮。  
  
##  <a name="a-nameonreplacealla--ceditviewonreplaceall"></a><a name="onreplaceall"></a>CEditView::OnReplaceAll  
 `CEditView`调用`OnReplaceAll`当用户在标准替换对话框中选择全部替换按钮。  
  
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
 `OnReplaceAll`搜索指定的文本的缓冲区中的文本`lpszFind`，与由指定的大小写区分功能`bCase`。 在当前所选内容的开头开始搜索。 每次找到搜索文本，则此函数会将该出现的文本替换与指定的文本`lpszReplace`。 搜索通过调用[FindText](#findtext)。 在默认实现中， [OnTextNotFound](#ontextnotfound)如果没有找到文本，则调用。  
  
 如果当前所选内容不匹配`lpszFind`，所选内容更新为指定的文本的第一个匹配项`lpszFind`并且不执行替换操作。 这允许用户以确认这是他们想要选择与要替换的文本不匹配时执行的操作。  
  
 重写`OnReplaceAll`更改的方式`CEditView`-派生的对象替换文本。  
  
##  <a name="a-nameonreplacesela--ceditviewonreplacesel"></a><a name="onreplacesel"></a>CEditView::OnReplaceSel  
 `CEditView`调用`OnReplaceSel`当用户在标准替换对话框中选择替换按钮。  
  
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
 指定搜索方向。 如果**TRUE**，搜索方向将是朝向缓冲区的末尾。 如果**FALSE**，搜索方向将是朝向该缓冲区的开头。  
  
 `bCase`  
 指定该搜索是否区分大小写。 如果**TRUE**，搜索不区分大小写。 如果**FALSE**，搜索不区分大小写。  
  
 `lpszReplace`  
 要替换所找到的文本的文本。  
  
### <a name="remarks"></a>备注  
 替换之后所选内容，此函数搜索的文本中指定的文本的下一个匹配项的缓冲区`lpszFind`，在指定的方向`bNext`，与由指定的大小写区分功能`bCase`。 搜索通过调用[FindText](#findtext)。 如果未找到文本， [OnTextNotFound](#ontextnotfound)调用。  
  
 重写`OnReplaceSel`更改的方式`CEditView`-派生的对象替换选定的文本。  
  
##  <a name="a-nameontextnotfounda--ceditviewontextnotfound"></a><a name="ontextnotfound"></a>CEditView::OnTextNotFound  
 重写此函数可更改默认实现中，将调用 Windows 函数**MessageBeep**。  
  
```  
virtual void OnTextNotFound(LPCTSTR lpszFind);
```  
  
### <a name="parameters"></a>参数  
 `lpszFind`  
 要找的文本。  
  
##  <a name="a-nameprintinsiderecta--ceditviewprintinsiderect"></a><a name="printinsiderect"></a>CEditView::PrintInsideRect  
 调用`PrintInsideRect`以在指定的矩形中打印文本*rectLayout*。  
  
```  
UINT PrintInsideRect(
    CDC *pDC,  
    RECT& rectLayout,  
    UINT nIndexStart,  
    UINT nIndexStop);
```  
  
### <a name="parameters"></a>参数  
 `pDC`  
 指向打印机设备上下文指针。  
  
 *rectLayout*  
 引用[CRect](../../atl-mfc-shared/reference/crect-class.md)对象或[RECT 结构](../../mfc/reference/rect-structure1.md)指定是用来呈现文本的矩形。  
  
 `nIndexStart`  
 要呈现的第一个字符缓冲区中的索引。  
  
 `nIndexStop`  
 在后面要呈现的最后一个字符的字符缓冲区中的索引。  
  
### <a name="return-value"></a>返回值  
 要打印的下一个字符的索引 （也就是说，呈现的最后一个字符后面的字符的字符）。  
  
### <a name="remarks"></a>备注  
 如果`CEditView`控件不具有该样式**ES_AUTOHSCROLL**，呈现矩形内文本换行。 如果该控件没有样式**ES_AUTOHSCROLL**，文本将被剪裁的矩形的右边缘。  
  
 **Rect.bottom**元素*rectLayout*对象进行更改，因此该矩形的尺寸定义原始文本所占用的矩形的一部分。  
  
##  <a name="a-nameserializerawa--ceditviewserializeraw"></a><a name="serializeraw"></a>CEditView::SerializeRaw  
 调用`SerializeRaw`能够`CArchive`对象读取或写入的文本`CEditView`对象传递给一个文本文件。  
  
```  
void SerializeRaw(CArchive& ar);
```  
  
### <a name="parameters"></a>参数  
 `ar`  
 引用`CArchive`对象，它存储序列化的文本。  
  
### <a name="remarks"></a>备注  
 `SerializeRaw`不同于`CEditView`的内部实现`Serialize`在于它读取和写入纯文本，而无需前面对象说明数据。  
  
##  <a name="a-namesetprinterfonta--ceditviewsetprinterfont"></a><a name="setprinterfont"></a>CEditView::SetPrinterFont  
 调用`SetPrinterFont`到由指定的字体设置的打印机字体`pFont`。  
  
```  
void SetPrinterFont(CFont* pFont);
```  
  
### <a name="parameters"></a>参数  
 `pFont`  
 指向类型的对象的指针`CFont`。 如果**NULL**，用于打印的字体开始算起的显示字体。  
  
### <a name="remarks"></a>备注  
 如果您想让视图始终使用特定字体进行打印，包括对`SetPrinterFont`在您的类`OnPreparePrinting`函数。 此调用虚函数之前打印发生，因此字体更改发生之前打印视图的内容。  
  
##  <a name="a-namesettabstopsa--ceditviewsettabstops"></a><a name="settabstops"></a>CEditView::SetTabStops  
 调用此函数可设置用于显示和打印的制表位。  
  
```  
void SetTabStops(int nTabStops);
```  
  
### <a name="parameters"></a>参数  
 `nTabStops`  
 每个制表位，对话框单位的宽度。  
  
### <a name="remarks"></a>备注  
 支持只是一个单一的制表位宽度。 (`CEdit`对象支持多个选项卡宽度。)宽度是字体的采用对话框单位等于&1; /&4; 的打印或显示时所用的平均字符宽度 （基于大写和小写字母字符）。 不应使用`CEdit::SetTabStops`因为`CEditView`必须缓存的制表位值。  
  
 此函数修改仅为其调用的对象的选项卡。 若要更改选项卡停止每个`CEditView`对象在您的应用程序，请调用每个对象的`SetTabStops`函数。  
  
### <a name="example"></a>示例  
 此代码段通过仔细测量该控件使用的字体对每个第四个字符控件中设置制表位。  
  
 [!code-cpp[NVC_MFCDocView #&67;](../../mfc/codesnippet/cpp/ceditview-class_3.cpp)]  
  
##  <a name="a-nameunlockbuffera--ceditviewunlockbuffer"></a><a name="unlockbuffer"></a>CEditView::UnlockBuffer  
 调用该成员函数以解锁缓冲区。  
  
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

