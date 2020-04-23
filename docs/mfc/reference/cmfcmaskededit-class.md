---
title: CMFCMaskedEdit 类
ms.date: 11/04/2016
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
ms.openlocfilehash: 26617f10605fe2a8a94adcc477cccab7e2ba4919
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754221"
---
# <a name="cmfcmaskededit-class"></a>CMFCMaskedEdit 类

该`CMFCMaskedEdit`类支持屏蔽编辑控件，该控件根据掩码验证用户输入，并根据模板显示已验证的结果。

## <a name="syntax"></a>语法

```
class CMFCMaskedEdit : public CEdit
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|`CMFCMaskedEdit::CMFCMaskedEdit`|默认构造函数。|
|`CMFCMaskedEdit::~CMFCMaskedEdit`|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CMFC蒙面编辑：:D可屏蔽](#disablemask)|禁用验证用户输入。|
|[CMFC扫描编辑：仅启用"只启用"扫描字符"](#enablegetmaskedcharsonly)|指定`GetWindowText`方法是否仅检索蒙版字符。|
|[CMFC蒙面编辑：：启用蒙版](#enablemask)|初始化蒙版编辑控件。|
|[CMFCSsedit：：启用选择分组](#enableselectbygroup)|指定屏蔽编辑控件是选择特定用户输入组还是所有用户输入。|
|[CMFC蒙面编辑：仅启用SetSet](#enablesetmaskedcharsonly)|指定文本是仅针对蒙版字符验证的，还是针对整个掩码验证的。|
|`CMFCMaskedEdit::GetThisClass`|框架用于获取指向与此类类型关联的[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)对象的指针。|
|[CMFCSsedit 编辑：获取窗口文本](#getwindowtext)|从蒙版编辑控件检索已验证的文本。|
|[CMFC扫描编辑：：设置有效字符](#setvalidchars)|指定用户可以输入的有效字符字符串。|
|[CMFCSsedit：设置窗口文本](#setwindowtext)|在蒙版编辑控件中显示提示。|

### <a name="protected-methods"></a>受保护的方法

|名称|说明|
|----------|-----------------|
|[CMFC蒙面编辑：：被蒙塞查尔](#ismaskedchar)|由框架调用，以根据相应的掩码字符验证指定的字符。|

## <a name="remarks"></a>备注

执行以下步骤以在`CMFCMaskedEdit`应用程序中使用控件：

1. 将`CMFCMaskedEdit`对象嵌入到窗口类中。

2. 调用[CMFCMaskedEdit：：启用蒙版](#enablemask)方法以指定掩码。

3. 调用[CMFCMaskedEdit：：设置 ValidChars](#setvalidchars)方法以指定有效字符的列表。

4. 调用[CMFCMaskedEdit：：SetWindowText](#setwindowtext)方法以指定蒙版编辑控件的默认文本。

5. 调用[CMFC"解密：：获取窗口文本](#getwindowtext)"方法以检索已验证的文本。

如果不调用一个或多个方法初始化蒙版、有效字符和默认文本，则蒙版编辑控件的操作与标准编辑控件一样。

## <a name="example"></a>示例

下面的示例演示如何通过使用`EnableMask`方法为蒙版编辑控件创建掩码来设置掩码（例如电话号码），说明用户可以输入的有效字符字符串`SetValidChars`的方法，以及`SetWindowText`在蒙版编辑控件中显示提示的方法。 此示例是["新控件"示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_NewControls#11](../../mfc/reference/codesnippet/cpp/cmfcmaskededit-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#12](../../mfc/reference/codesnippet/cpp/cmfcmaskededit-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CEdit](../../mfc/reference/cedit-class.md)

[CMFCMaskedEdit](../../mfc/reference/cmfcmaskededit-class.md)

## <a name="requirements"></a>要求

**标题：** afx 蒙面编辑.h

## <a name="cmfcmaskededitdisablemask"></a><a name="disablemask"></a>CMFC蒙面编辑：:D可屏蔽

禁用验证用户输入。

```cpp
void DisableMask();
```

### <a name="remarks"></a>备注

如果禁用用户输入验证，则蒙版编辑控件的表示方式类似于标准编辑控件。

## <a name="cmfcmaskededitenablegetmaskedcharsonly"></a><a name="enablegetmaskedcharsonly"></a>CMFC扫描编辑：仅启用"只启用"扫描字符"

指定`GetWindowText`方法是否仅检索蒙版字符。

```cpp
void EnableGetMaskedCharsOnly(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>参数

*b 启用*<br/>
[在]TRUE 指定[CMFC 蒙面编辑：：获取窗口文本](#getwindowtext)方法仅检索蒙版字符;FALSE 以指定 该方法检索整个文本。 默认值为 TRUE。

### <a name="remarks"></a>备注

使用此方法可启用检索蒙版字符。 然后创建与电话号码对应的屏蔽编辑控件，例如 （425） 555-0187。 如果调用 方法`GetWindowText`，它将返回"4255550187"。 如果禁用检索蒙版字符，`GetWindowText`该方法将返回编辑控件中显示的文本，例如"（425） 555-0187"。

## <a name="cmfcmaskededitenablemask"></a><a name="enablemask"></a>CMFC蒙面编辑：：启用蒙版

初始化蒙版编辑控件。

```cpp
void EnableMask(
    LPCTSTR lpszMask,
    LPCTSTR lpszInputTemplate,
    TCHAR chMaskInputTemplate=_T('_'),
    LPCTSTR lpszValid=NULL);
```

### <a name="parameters"></a>参数

*lpsz Mask*<br/>
[在]指定可在用户输入中的每个位置显示的字符类型的掩码字符串。 *lpszInputTemplate*和*lpszMask*参数字符串的长度必须相同。 有关蒙版字符的更多详细信息，请参阅备注部分。

*lpszInput模板*<br/>
[在]一个掩码模板字符串，用于指定可在用户输入中的每个位置显示的文本字符。 使用下划线字符 （''） 作为字符占位符。 *lpszInputTemplate*和*lpszMask*参数字符串的长度必须相同。

*chMask输入模板*<br/>
[在]框架替换为用户输入中每个无效字符的默认字符。 此参数的默认值为下划线 （"*"。

*lpsz 有效*<br/>
[在]包含一组有效字符的字符串。 NULL 表示所有字符都有效。 此参数的默认值为 NULL。

### <a name="remarks"></a>备注

使用此方法为蒙版编辑控件创建掩码。 从`CMFCMaskedEdit`类派生类并重写[CMFCEdit：：IsMaskedChar](#ismaskedchar)方法，以使用您自己的代码进行自定义掩码处理。

下表列出了默认掩码字符：

|蒙版字符|定义|
|--------------------|----------------|
|D|数字。|
|d|数字或空格。|
|+|加上（'+'），减（'-'）或空格。|
|C|字母字符。|
|c|字母字符或空格。|
|A|字母数字字符。|
|a|字母数字字符或空格。|
|*|可打印字符。|

## <a name="cmfcmaskededitenableselectbygroup"></a><a name="enableselectbygroup"></a>CMFCSsedit：：启用选择分组

指定蒙版编辑控件是否允许用户选择特定的组输入或所有输入。

```cpp
void EnableSelectByGroup(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>参数

*b 启用*<br/>
[在]TRUE 仅选择组;FALSE 以选择整个文本。 默认值为 TRUE。

### <a name="remarks"></a>备注

使用此函数可以指定蒙版编辑控件是允许用户按组还是整个文本进行选择。

默认情况下，启用按组选择。 在这种情况下，用户只能选择连续的有效字符组。

例如，可以使用以下蒙版编辑控件来验证电话号码：

```cpp
m_wndMaskEdit.EnableMask(
    _T(" ddd  ddd dddd"),  // Mask string
    _T("(___) ___-____"),  // Template string
    _T(' '));              // Default char

m_wndMaskEdit.SetValidChars(NULL); // All characters are valid.

m_wndMaskEdit.SetWindowText(_T("(425) 555-0187")); // Prompt
```

如果启用了按组选择，则用户只能检索"425"、"555"或"0187"字符串组。 如果组选择被禁用，用户可以检索电话号码的整个文本："（425） 555-0187"。

## <a name="cmfcmaskededitenablesetmaskedcharsonly"></a><a name="enablesetmaskedcharsonly"></a>CMFC蒙面编辑：仅启用SetSet

指定文本是仅针对蒙版字符验证的，还是针对整个掩码验证的。

```cpp
void EnableSetMaskedCharsOnly(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>参数

*b 启用*<br/>
[在]TRUE 以仅根据蒙版字符验证用户输入;FALSE 以验证整个掩码。 默认值为 TRUE。

## <a name="cmfcmaskededitgetwindowtext"></a><a name="getwindowtext"></a>CMFCSsedit 编辑：获取窗口文本

从蒙版编辑控件检索已验证的文本。

```
int GetWindowText(
    LPTSTR lpszStringBuf,
    int nMaxCount) const;

void GetWindowText(CString& rstrString) const;
```

### <a name="parameters"></a>参数

*lpszStringBuf*<br/>
[出]指向从编辑控件接收文本的缓冲区的指针。

*nMaxCount*<br/>
[在]要接收的最大字符数。

*rstrString*<br/>
[出]对从编辑控件接收文本的字符串对象的引用。

### <a name="return-value"></a>返回值

第一个方法重载返回复制到*lpszStringBuf*参数缓冲区的字符串的字节数;如果蒙版编辑控件没有文本，则为 0。

### <a name="remarks"></a>备注

此方法将文本从蒙版编辑控件复制到*lpszStringBuf*缓冲区或*rstrString 字符串*。

此方法重新定义[了 CWnd：：getWindowText](../../mfc/reference/cwnd-class.md#getwindowtext)。

## <a name="cmfcmaskededitismaskedchar"></a><a name="ismaskedchar"></a>CMFC蒙面编辑：：被蒙塞查尔

由框架调用，以根据相应的掩码字符验证指定的字符。

```
virtual BOOL IsMaskedChar(
    TCHAR chChar,
    TCHAR chMaskChar) const;
```

### <a name="parameters"></a>参数

*chChar*<br/>
[在]要验证的字符。

*chMaskChar*<br/>
[在]掩码字符串中的相应字符。

### <a name="return-value"></a>返回值

如果*chChar*参数是*chMaskChar*参数允许的字符类型，则为 TRUE;否则，FALSE。

### <a name="remarks"></a>备注

重写此方法以自行验证输入字符。 有关蒙版字符的详细信息，请参阅[CMFCEdit：：启用掩码](#enablemask)方法。

## <a name="cmfcmaskededitsetvalidchars"></a><a name="setvalidchars"></a>CMFC扫描编辑：：设置有效字符

指定用户可以输入的有效字符字符串。

```cpp
void SetValidChars(LPCTSTR lpszValid=NULL);
```

### <a name="parameters"></a>参数

*lpsz 有效*<br/>
[在]包含有效输入字符集的字符串。 NULL 表示所有字符都有效。 此参数的默认值为 NULL。

### <a name="remarks"></a>备注

使用此方法定义有效字符的列表。 如果输入字符不在此列表中，则屏蔽编辑控件将不接受它。

以下代码示例仅接受十六进制数字。

```cpp
//Mask: 0xFFFF
m_wndMaskEdit.EnableMask(
    _T(" AAAA"),                // The mask string.
    _T("0x____"),               // The literal template string.
    _T('_'));                   // The default character that
                                // replaces the backspace character.
// Valid string characters
m_wndMaskEdit.SetValidChars(_T("1234567890ABCDEFabcdef"));m_wndMaskEdit.SetWindowText(_T("0x01AF"));
```

## <a name="cmfcmaskededitsetwindowtext"></a><a name="setwindowtext"></a>CMFCSsedit：设置窗口文本

在蒙版编辑控件中显示提示。

```cpp
void SetWindowText(LPCTSTR lpszString);
```

### <a name="parameters"></a>参数

*lpszString*<br/>
[在]指向将用作提示的 null 终止字符串。

### <a name="remarks"></a>备注

此方法设置控件文本。

此方法重新定义[CWnd：setWindowText](../../mfc/reference/cwnd-class.md#setwindowtext)。

## <a name="see-also"></a>请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CEdit Class](../../mfc/reference/cedit-class.md)
