---
title: CString 格式设置和消息框显示
ms.date: 11/04/2016
helpviewer_keywords:
- CString objects [MFC], formatting and message boxes
ms.assetid: d1068cf4-9cc5-4952-b9e7-d612c53cbc28
ms.openlocfilehash: fa1fe8826543834872de5257a0f5d56b2ad9fc1c
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752681"
---
# <a name="cstring-formatting-and-message-box-display"></a>CString 格式设置和消息框显示

提供了许多函数来格式化和分析`CString`对象。 只要必须操作`CString`对象，都可以使用这些函数，但它们对于设置将显示在消息框文本中的字符串的格式特别有用。

这组函数还包括用于显示消息框的全局例程。

### <a name="cstring-functions"></a>CString 函数

|||
|-|-|
|[AfxExtractSubString](#afxextractsubstring)|从给定源字符串中提取由单个字符分隔的子字符串。|
|[AfxFormatString1](#afxformatstring1)|将给定字符串替换为字符串表中包含的字符串中的格式字符"%1"。|
|[AfxFormatString2](#afxformatstring2)|用两个字符串替换字符串表中的格式字符"%1"和"%2"。|
|[AfxMessageBox](#afxmessagebox)|显示消息框。|

### <a name="requirements"></a>要求

  **头**afxwin.h

## <a name="afxextractsubstring"></a><a name="afxextractsubstring"></a>Afx提取子字符串

此全局函数可用于从给定源字符串中提取子字符串。

```
BOOL AFXAPI AfxExtractSubString (
    CString& rString,
    LPCTSTR lpszFullString,
    int iSubString,
    TCHAR chSep  = '\n');
```

### <a name="parameters"></a>参数

*rString*<br/>
对将收到单个子字符串的[CString](../../atl-mfc-shared/using-cstring.md)对象的引用。

*lpsz全字符串*<br/>
包含要提取的字符串的全文。

*iSubString*<br/>
从*lpszFullString*中提取的子字符串的零基索引。

*chSep*<br/>
分隔符字符用于分隔子字符串。

### <a name="return-value"></a>返回值

如果函数成功提取了提供的索引上的子字符串，则为 TRUE;否则，FALSE。

### <a name="remarks"></a>备注

当已知的单个字符分隔每个子字符串时，此功能可用于从源字符串中提取多个子字符串。 每次调用*lpszFullString*参数时，此函数都会从开始搜索。

如果*lpszFullString*设置为 NULL，或者该函数到达*lpszFullString*的末尾而不查找指定分隔符字符的*iSubString*+1 匹配项，则此功能将返回 FALSE。 如果将*lpszFullString*设置为 NULL，则*rString*参数将不会从其原始值修改;否则，如果无法为指定的索引提取子字符串，则*rString*参数将设置为空字符串。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_Utilities#48](../../mfc/codesnippet/cpp/cstring-formatting-and-message-box-display_1.cpp)]

### <a name="requirements"></a>要求

  **头**afxwin.h

## <a name="afxformatstring1"></a><a name="afxformatstring1"></a>AfxFormatString1

将*lpsz1*指向的字符串替换为*nIDS*标识的模板字符串资源中字符"%1"的任何实例。

```cpp
void  AfxFormatString1(
    CString& rString,
    UINT nIDS,
    LPCTSTR lpsz1);
```

### <a name="parameters"></a>参数

*rString*<br/>
对在执行替换后将包含生成字符串的 `CString` 对象的引用。

*Nids*<br/>
将对其执行替换的模板字符串的资源 ID。

*lpsz1*<br/>
将替换模板字符串中的格式字符串“%1”的字符串。

### <a name="remarks"></a>备注

新形成的字符串存储在*rString*中。 例如，如果字符串表中的字符串为"找不到文件 %1"，并且*lpsz1*等于"C：\MYFILE"。TXT"，然后*rString*将包含字符串"文件C：\MYFILE。未找到 TXT"。 此函数对为发送到消息框和其他窗口的字符串设置格式很有用。

如果格式字符“%1”多次出现在字符串中，则将执行多次替换。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_Utilities#25](../../mfc/codesnippet/cpp/cstring-formatting-and-message-box-display_2.cpp)]

### <a name="requirements"></a>要求

  **头**afxwin.h

## <a name="afxformatstring2"></a><a name="afxformatstring2"></a>AfxFormatString2

将*lpsz1*指向的字符串替换为字符"%1"的任何实例，以及*lpsz2*指向字符"%2"的任何实例的字符串，该字符串位于*nIDS*标识的模板字符串资源中。

```cpp
void AfxFormatString2(
    CString& rString,
    UINT nIDS,
    LPCTSTR lpsz1,
    LPCTSTR lpsz2);
```

### <a name="parameters"></a>参数

*rString*<br/>
执行替换后将`CString`包含结果字符串的 对 的 引用。

*Nids*<br/>
将在其上执行替换的模板字符串的字符串表 ID。

*lpsz1*<br/>
将替换模板字符串中的格式字符串“%1”的字符串。

*lpsz2*<br/>
将替换模板字符串中的格式字符"%2"的字符串。

### <a name="remarks"></a>备注

新形成的字符串存储在*rString*中。 例如，如果字符串表中的字符串是"在目录 %2 中找不到文件 %1"，*则 lpsz1*指向"MYFILE"。*TXT"，lpsz2*指向"C：_MYDIR"，然后*rString*将包含字符串"文件MYFILE"。目录 C 中找不到 TXT：\MYDIR"

如果格式字符"%1"或"%2"在字符串中多次显示，则进行多次替换。 它们不必按数字顺序排列。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_Utilities#26](../../mfc/codesnippet/cpp/cstring-formatting-and-message-box-display_3.cpp)]

### <a name="requirements"></a>要求

  **头**afxwin.h

## <a name="afxmessagebox"></a><a name="afxmessagebox"></a>AfxMessageBox

屏幕上显示一个消息框。

```
int AfxMessageBox(
    LPCTSTR lpszText,
    UINT nType = MB_OK,
    UINT nIDHelp = 0);

int AFXAPI AfxMessageBox(
    UINT nIDPrompt,
    UINT nType = MB_OK,
    UINT nIDHelp = (UINT) -1);
```

### <a name="parameters"></a>参数

*lpszText*<br/>
指向包含`CString`要在消息框中显示的消息的对象或空端结束的字符串。

nType**<br/>
消息框的样式。 将任何[消息框样式](../../mfc/reference/styles-used-by-mfc.md#message-box-styles)应用于该框。

*nIDHelp*<br/>
邮件的帮助上下文 ID;0 表示将使用应用程序的默认帮助上下文。

*nID提示*<br/>
用于引用字符串表中的字符串的唯一 ID。

### <a name="return-value"></a>返回值

如果内存不足以显示消息框，则为零;否则，返回以下值之一：

- 选择中止按钮。

- IDCANCEL"取消"按钮已选定。

- 已选择"忽略"按钮。

- IDNO "没有"按钮已选中。

- IDOK 已选择"确定"按钮。

- 选择重试按钮。

- IDYES 选择"是"按钮。

如果消息框具有"取消"按钮，则如果按下 ESC 键或选择"取消"按钮，则将返回 IDCANCEL 值。 如果消息框没有"取消"按钮，则按下 ESC 键不起作用。

函数[AfxFormatString1](#afxformatstring1)和[AfxFormatString2](#afxformatstring2)可用于设置消息框中显示的文本的格式。

### <a name="remarks"></a>备注

此重载函数的第一种形式在消息框中显示*lpszText*指向的文本字符串，并使用*nIDHelp*来描述帮助上下文。 当用户按下帮助键（通常是 F1）时，帮助上下文用于跳转到关联的帮助主题。

函数的第二种形式使用带有 ID *nIDPrompt 的*字符串资源在消息框中显示一条消息。 关联的帮助页面通过*nIDHelp*的值找到。 如果使用*nIDHelp*的默认值 （-1），则字符串资源 ID *nIDPrompt*将用于帮助上下文。 有关定义帮助上下文的详细信息，请参阅[技术说明 28](../../mfc/tn028-context-sensitive-help-support.md)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#133](../../mfc/reference/codesnippet/cpp/cstring-formatting-and-message-box-display_4.cpp)]

## <a name="see-also"></a>另请参阅

[MFC 宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)<br/>
[CStringT 类](../../atl-mfc-shared/reference/cstringt-class.md)
