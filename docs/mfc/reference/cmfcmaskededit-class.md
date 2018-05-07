---
title: CMFCMaskedEdit 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCMaskedEdit
- AFXMASKEDEDIT/CMFCMaskedEdit
- AFXMASKEDEDIT/CMFCMaskedEdit::DisableMask
- AFXMASKEDEDIT/CMFCMaskedEdit::EnableGetMaskedCharsOnly
- AFXMASKEDEDIT/CMFCMaskedEdit::EnableMask
- AFXMASKEDEDIT/CMFCMaskedEdit::EnableSelectByGroup
- AFXMASKEDEDIT/CMFCMaskedEdit::EnableSetMaskedCharsOnly
- AFXMASKEDEDIT/CMFCMaskedEdit::GetWindowText
- AFXMASKEDEDIT/CMFCMaskedEdit::SetValidChars
- AFXMASKEDEDIT/CMFCMaskedEdit::SetWindowText
- AFXMASKEDEDIT/CMFCMaskedEdit::IsMaskedChar
dev_langs:
- C++
helpviewer_keywords:
- CMFCMaskedEdit [MFC], DisableMask
- CMFCMaskedEdit [MFC], EnableGetMaskedCharsOnly
- CMFCMaskedEdit [MFC], EnableMask
- CMFCMaskedEdit [MFC], EnableSelectByGroup
- CMFCMaskedEdit [MFC], EnableSetMaskedCharsOnly
- CMFCMaskedEdit [MFC], GetWindowText
- CMFCMaskedEdit [MFC], SetValidChars
- CMFCMaskedEdit [MFC], SetWindowText
- CMFCMaskedEdit [MFC], IsMaskedChar
ms.assetid: 13b1a645-2d5d-4c37-8599-16d5003f23a5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 985cd4011dbb1ea8ccad7cd40c81833dd5507f11
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="cmfcmaskededit-class"></a>CMFCMaskedEdit 类
`CMFCMaskedEdit`类支持掩码的编辑控件，将验证用户输入掩码并显示根据模板验证的结果。  
  
## <a name="syntax"></a>语法  
  
```  
class CMFCMaskedEdit : public CEdit  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|`CMFCMaskedEdit::CMFCMaskedEdit`|默认构造函数。|  
|`CMFCMaskedEdit::~CMFCMaskedEdit`|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCMaskedEdit::DisableMask](#disablemask)|禁用验证用户输入。|  
|[CMFCMaskedEdit::EnableGetMaskedCharsOnly](#enablegetmaskedcharsonly)|指定是否`GetWindowText`方法检索仅掩码的字符。|  
|[CMFCMaskedEdit::EnableMask](#enablemask)|初始化掩码编辑控件。|  
|[CMFCMaskedEdit::EnableSelectByGroup](#enableselectbygroup)|指定是否掩码的编辑控件选择的用户输入或输入的所有用户的特定组。|  
|[CMFCMaskedEdit::EnableSetMaskedCharsOnly](#enablesetmaskedcharsonly)|指定是否根据验证文本，仅屏蔽字符，或针对整个掩码。|  
|`CMFCMaskedEdit::GetThisClass`|由框架用于获取指向的指针[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)与此类类型关联的对象。|  
|[CMFCMaskedEdit::GetWindowText](#getwindowtext)|检索验证从掩码的编辑控件的文本。|  
|[CMFCMaskedEdit::SetValidChars](#setvalidchars)|指定用户可以输入的有效字符的字符串。|  
|[CMFCMaskedEdit::SetWindowText](#setwindowtext)|掩码的编辑控件中显示一条提示。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCMaskedEdit::IsMaskedChar](#ismaskedchar)|由框架调用以验证对相应的掩码字符的指定的字符。|  
  
## <a name="remarks"></a>备注  
 执行以下步骤以使用`CMFCMaskedEdit`应用程序中的控件：  
  
 1. 嵌入`CMFCMaskedEdit`入窗口类的对象。  
  
 2. 调用[CMFCMaskedEdit::EnableMask](#enablemask)方法，以指定掩码。  
  
 3. 调用[CMFCMaskedEdit::SetValidChars](#setvalidchars)方法，以指定有效的列表。  
  
 4. 调用[CMFCMaskedEdit::SetWindowText](#setwindowtext)若指定的默认文本在掩蔽的编辑控件的方法。  
  
 5. 调用[CMFCMaskedEdit::GetWindowText](#getwindowtext)方法来检索已验证的文本。  
  
 如果不调用以初始化掩码、 有效字符和默认文本的一个或多个方法，掩码的编辑控件的行为就像该标准编辑控件的行为。  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用设置掩码 （例如电话号码）`EnableMask`方法来为掩码编辑控件，创建掩码`SetValidChars`方法，以指定的用户可以输入的有效字符和字符串`SetWindowText` edit 控件的方法以在掩蔽显示一条提示。 此示例摘自[新控件示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_NewControls#11](../../mfc/reference/codesnippet/cpp/cmfcmaskededit-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls#12](../../mfc/reference/codesnippet/cpp/cmfcmaskededit-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CEdit](../../mfc/reference/cedit-class.md)  
  
 [CMFCMaskedEdit](../../mfc/reference/cmfcmaskededit-class.md)  
  
## <a name="requirements"></a>要求  
 **标头：** afxmaskededit.h  
  
##  <a name="disablemask"></a>  CMFCMaskedEdit::DisableMask  
 禁用验证用户输入。  
  
```  
void DisableMask();
```  
  
### <a name="remarks"></a>备注  
 如果禁用的用户输入的验证，则掩码的编辑控件的行为像标准编辑控件。  
  
##  <a name="enablegetmaskedcharsonly"></a>  CMFCMaskedEdit::EnableGetMaskedCharsOnly  
 指定是否`GetWindowText`方法检索仅掩码的字符。  
  
```  
void EnableGetMaskedCharsOnly(BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bEnable`  
 `TRUE` 若要指定[CMFCMaskedEdit::GetWindowText](#getwindowtext)方法检索仅屏蔽字符;`FALSE`若要指定方法检索整个文本。 默认值为 `TRUE`。  
  
### <a name="remarks"></a>备注  
 此方法用于启用检索掩码的字符。 然后创建对应的电话号码，例如 (425) 555-0187 的掩码的编辑控件。 如果调用`GetWindowText`方法，则返回"4255550187"。 如果你禁用检索掩码的字符`GetWindowText`方法返回编辑控件，例如"(425) 555-0187"中显示的文本。  
  
##  <a name="enablemask"></a>  CMFCMaskedEdit::EnableMask  
 初始化掩码编辑控件。  
  
```  
void EnableMask(
    LPCTSTR lpszMask,  
    LPCTSTR lpszInputTemplate,  
    TCHAR chMaskInputTemplate=_T('_'),  
    LPCTSTR lpszValid=NULL);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszMask`  
 指定的字符可以出现在用户输入中每个位置的类型掩码字符串。 长度`lpszInputTemplate`和`lpszMask`参数字符串必须相同。 请参阅有关掩码字符的更多详细信息备注部分。  
  
 [in] `lpszInputTemplate`  
 一个掩码模板字符串，指定文本字符可以出现在用户输入中每个位置。 使用下划线字符 ('_') 作为的字符占位符。 长度`lpszInputTemplate`和`lpszMask`参数字符串必须相同。  
  
 [in] `chMaskInputTemplate`  
 框架将为每个用户输入中包含无效字符替换默认字符。 此参数的默认值是下划线 ('_')。  
  
 [in] `lpszValid`  
 包含一组有效字符的字符串。 `NULL` 指示所有字符都有效。 此参数的默认值为 `NULL`。  
  
### <a name="remarks"></a>备注  
 此方法用于创建掩码的编辑控件的掩码。 从派生类`CMFCMaskedEdit`类并重写[CMFCMaskedEdit::IsMaskedChar](#ismaskedchar)你自己的代码用于自定义掩码处理方法。  
  
 下表列出了默认掩码字符：  
  
|掩码字符|定义|  
|--------------------|----------------|  
|D|数字。|  
|d|数字或空格。|  
|+|加 （+）、 减号 (-)，或空间。|  
|C|字母字符。|  
|c|字母字符或空格。|  
|包含当前请求的 URL 的|字母数字字符。|  
|a|字母数字字符或空格。|  
|*|可打印字符。|  
  
##  <a name="enableselectbygroup"></a>  CMFCMaskedEdit::EnableSelectByGroup  
 指定掩码的编辑控件是否允许用户选择的特定组输入或所有输入。  
  
```  
void EnableSelectByGroup(BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bEnable`  
 `TRUE` 若要选择仅组;`FALSE`来选择整个文本。 默认值为 `TRUE`。  
  
### <a name="remarks"></a>备注  
 使用此函数指定掩码的编辑控件是否允许用户通过组或整个文本选择。  
  
 默认情况下，启用选择的组。 在这种情况下用户可以选择仅连续组的有效字符。  
  
 例如，可以使用以下掩码的编辑控件来验证的电话号码：  
  
 `m_wndMaskEdit.EnableMask(`  
  
 `_T(" ddd  ddd dddd"),// Mask string`  
  
 `_T("(___) ___-____"),// Template string`  
  
 `_T(' '));// Default char`  
  
 `m_wndMaskEdit.SetValidChars(NULL); // All characters are valid.`  
  
 `m_wndMaskEdit.SetWindowText(_T("(425) 555-0187")); // Prompt`  
  
 如果启用了按组选择，用户可以检索仅"425"、"555"或"0187"字符串组。 如果禁用组选择用户可以在检索的电话号码的整个文本:"(425) 555-0187"。  
  
##  <a name="enablesetmaskedcharsonly"></a>  CMFCMaskedEdit::EnableSetMaskedCharsOnly  
 指定对仅经过屏蔽的字符，或针对整个掩码是否验证文本。  
  
```  
void EnableSetMaskedCharsOnly(BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bEnable`  
 `TRUE` 若要验证用户输入与仅屏蔽字符;`FALSE`以对整个掩码进行验证。 默认值为 `TRUE`。  
  
##  <a name="getwindowtext"></a>  CMFCMaskedEdit::GetWindowText  
 检索验证从掩码的编辑控件的文本。  
  
```  
int GetWindowText(
    LPTSTR lpszStringBuf,  
    int nMaxCount) const;  
  
void GetWindowText(CString& rstrString) const;  
```  
  
### <a name="parameters"></a>参数  
 [out] `lpszStringBuf`  
 指向接收来自编辑控件的文本的缓冲区的指针。  
  
 [in] `nMaxCount`  
 最大要接收的字符数。  
  
 [out] `rstrString`  
 对接收来自编辑控件的文本的字符串对象的引用。  
  
### <a name="return-value"></a>返回值  
 第一个方法重载方法返回的字符串复制到的字节数`lpszStringBuf`参数缓冲区; 如果掩码的编辑控件具有没有文本为 0。  
  
### <a name="remarks"></a>备注  
 此方法将文本复制到掩码的编辑控件从`lpszStringBuf`缓冲区或`rstrString`字符串。  
  
 此方法重新定义了[CWnd::GetWindowText](../../mfc/reference/cwnd-class.md#getwindowtext)。  
  
##  <a name="ismaskedchar"></a>  CMFCMaskedEdit::IsMaskedChar  
 由框架调用以验证对相应的掩码字符的指定的字符。  
  
```  
virtual BOOL IsMaskedChar(
    TCHAR chChar,  
    TCHAR chMaskChar) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `chChar`  
 要验证的字符。  
  
 [in] `chMaskChar`  
 掩码字符串中的相应字符。  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果`chChar`参数是一种通过允许的字符`chMaskChar`参数; 否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 重写此方法以验证自己的输入的字符。 有关掩码字符的详细信息，请参阅[CMFCMaskedEdit::EnableMask](#enablemask)方法。  
  
##  <a name="setvalidchars"></a>  CMFCMaskedEdit::SetValidChars  
 指定用户可以输入的有效字符的字符串。  
  
```  
void SetValidChars(LPCTSTR lpszValid=NULL);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszValid`  
 包含的一套有效的输入字符的字符串。 `NULL` 表示所有字符都有效。 此参数的默认值为 `NULL`。  
  
### <a name="remarks"></a>备注  
 使用此方法定义的有效字符的列表。 如果输入的字符不在此列表中，掩码的编辑控件将不会接受它。  
  
 下面的代码示例接受十六进制数字。  
  
 `//Mask: 0xFFFFm_wndMaskEdit.EnableMask( _T(" AAAA"),                // The mask string. _T("0x____"),               // The literal template string. _T('_'));                   // The default character that replaces the backspace character.// Valid string charactersm_wndMaskEdit.SetValidChars(_T("1234567890ABCDEFabcdef"));m_wndMaskEdit.SetWindowText(_T("0x01AF"));`  
  
##  <a name="setwindowtext"></a>  CMFCMaskedEdit::SetWindowText  
 掩码的编辑控件中显示一条提示。  
  
```  
void SetWindowText(LPCTSTR lpszString);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszString`  
 指向以 null 结尾的字符串，将使用作为提示。  
  
### <a name="remarks"></a>备注  
 此方法设置的控件文本。  
  
 此方法重新定义了[CWnd::SetWindowText](../../mfc/reference/cwnd-class.md#setwindowtext)。  
  
## <a name="see-also"></a>请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CEdit 类](../../mfc/reference/cedit-class.md)
