---
title: CString 格式设置和消息框显示
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.macros.strings
helpviewer_keywords:
- CString objects [MFC], formatting and message boxes
ms.assetid: d1068cf4-9cc5-4952-b9e7-d612c53cbc28
ms.openlocfilehash: fee8ba89605e6425b511407dab62be1f32e94a9d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62323786"
---
# <a name="cstring-formatting-and-message-box-display"></a>CString 格式设置和消息框显示

提供的许多功能进行格式化和分析`CString`对象。 可以使用这些函数，每当您必须操作`CString`对象，但它们是将出现在消息框文本的字符串设置格式特别有用。

此组的函数还包括用于显示一个消息框的全局例程。

### <a name="cstring-functions"></a>CString 函数

|||
|-|-|
|[AfxExtractSubString](#afxextractsubstring)|提取子字符串从给定的源字符串分隔的单个字符。|
|[AfxFormatString1](#afxformatstring1)|替换字符串中的格式字符"%1"的给定的字符串包含在字符串表中。|
|[AfxFormatString2](#afxformatstring2)|替换两个字符串的格式字符"%1"和"%2"在字符串中包含在字符串表中。|
|[AfxMessageBox](#afxmessagebox)|显示消息框。|

### <a name="requirements"></a>要求

  **标头**afxwin.h

##  <a name="afxextractsubstring"></a>  AfxExtractSubString

此全局函数可用于从给定的源字符串中提取子字符串。

```
BOOL AFXAPI AfxExtractSubString (
    CString& rString,
    LPCTSTR lpszFullString,
    int iSubString,
    TCHAR chSep  = '\n');
```

### <a name="parameters"></a>参数

*rString*<br/>
引用[CString](../../atl-mfc-shared/using-cstring.md)将收到单独的子字符串的对象。

*lpszFullString*<br/>
包含要从提取的字符串的完整文本的字符串。

*iSubString*<br/>
若要从提取的子字符串的从零开始的索引*lpszFullString*。

*chSep*<br/>
用于分隔子字符串的分隔符字符。

### <a name="return-value"></a>返回值

该函数成功提取的子字符串在提供的索引; 如果为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

此函数可用于源字符串中提取的多个子字符串时已知的单个字符用于分隔每个子字符串。 此函数将从开头搜索*lpszFullString*参数每次调用它。

此函数将返回 FALSE，如果任一*lpszFullString*设置为 NULL，或者该函数执行到末尾*lpszFullString*而无需查找*iSubString*+ 1指定的分隔符字符的出现次数。 *RString*参数如果不会从其原始值修改*lpszFullString*已设置为 NULL; 否则为*rString*参数设置为空字符串，如果无法为指定的索引中提取子字符串。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_Utilities#48](../../mfc/codesnippet/cpp/cstring-formatting-and-message-box-display_1.cpp)]

### <a name="requirements"></a>要求

  **标头**afxwin.h

##  <a name="afxformatstring1"></a>  AfxFormatString1

替换字符串指向*lpsz1*中所标识的模板字符串资源的字符"%1"的任何实例*nIDS*。

```
void  AfxFormatString1(
    CString& rString,
    UINT nIDS,
    LPCTSTR lpsz1);
```

### <a name="parameters"></a>参数

*rString*<br/>
对在执行替换后将包含生成字符串的 `CString` 对象的引用。

*nIDS*<br/>
将对其执行替换的模板字符串的资源 ID。

*lpsz1*<br/>
将替换模板字符串中的格式字符串“%1”的字符串。

### <a name="remarks"></a>备注

新构成的字符串存储在*rString*。 例如，如果字符串表中的字符串为"%1 找不到文件"，并*lpsz1*等于"C:\MYFILE。TXT"，然后*rString*将包含字符串"文件 C:\MYFILE。TXT 找不到的"。 此函数对为发送到消息框和其他窗口的字符串设置格式很有用。

如果格式字符“%1”多次出现在字符串中，则将执行多次替换。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_Utilities#25](../../mfc/codesnippet/cpp/cstring-formatting-and-message-box-display_2.cpp)]

### <a name="requirements"></a>要求

  **标头**afxwin.h

##  <a name="afxformatstring2"></a>  AfxFormatString2

替换字符串指向*lpsz1*字符"%1"的任何实例，指向的字符串*lpsz2*的任何实例中的模板字符串资源的字符"%2"由标识*nIDS*。

```
void AfxFormatString2(
    CString& rString,
    UINT nIDS,
    LPCTSTR lpsz1,
    LPCTSTR lpsz2);
```

### <a name="parameters"></a>参数

*rString*<br/>
对引用`CString`执行替换后将包含生成的字符串。

*nIDS*<br/>
将在其执行替换的模板字符串的字符串表 ID。

*lpsz1*<br/>
将替换模板字符串中的格式字符串“%1”的字符串。

*lpsz2*<br/>
一个字符串，将替换为格式字符"%2"的模板字符串中。

### <a name="remarks"></a>备注

新构成的字符串存储在*rString*。 例如，如果字符串表中的字符串为"%1 目录 %2 中找不到文件"， *lpsz1*指向"MYFILE。TXT"，并*lpsz2* "C:\MYDIR"，然后指向*rString*将包含字符串"文件 MYFILE。TXT C:\MYDIR 目录中找不到"

如果格式字符"%1"或"%2"不止一次出现在字符串中，将进行多个替换项。 它们无需按数值顺序。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_Utilities#26](../../mfc/codesnippet/cpp/cstring-formatting-and-message-box-display_3.cpp)]

### <a name="requirements"></a>要求

  **标头**afxwin.h

##  <a name="afxmessagebox"></a>  AfxMessageBox

在屏幕上显示一个消息框。

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
指向`CString`对象或包含在消息框中显示的消息的以 null 结尾的字符串。

*nType*<br/>
消息框的样式。 应用的任何[消息框样式](../../mfc/reference/styles-used-by-mfc.md#message-box-styles)给数字显示框。

*nIDHelp*<br/>
消息; 的帮助上下文 ID0 指示将使用应用程序的默认值帮助上下文。

*nIDPrompt*<br/>
用于引用字符串表中的字符串的唯一 ID。

### <a name="return-value"></a>返回值

如果不存在内存不足，无法显示消息框; 则为零否则，将返回以下值之一：

- 已选择 IDABORT 中止按钮。

- 已选择 IDCANCEL 取消按钮。

- 已选择 IDIGNORE 忽略按钮。

- 已选择 IDNO 否按钮。

- 已选择 IDOK 确定按钮。

- 已选择 IDRETRY 重试按钮。

- 已选择 IDYES 是按钮。

如果一个消息框包含取消按钮，如果按下了 ESC 键或选择取消按钮，将返回 IDCANCEL 值。 如果消息框没有取消按钮，按 ESC 键无效。

函数[AfxFormatString1](#afxformatstring1)并[AfxFormatString2](#afxformatstring2)在格式设置在消息框中显示的文本可能非常有用。

### <a name="remarks"></a>备注

第一种形式的此重载函数显示的文本字符串由指向*lpszText*消息框并使用*nIDHelp*来描述帮助上下文。 帮助上下文用于当用户按帮助键 (通常为 F1) 跳转到关联的帮助主题。

函数的第二种形式的 id 使用字符串资源*nIDPrompt*在消息框中显示一条消息。 关联的帮助页中的值可以找到*nIDHelp*。 如果默认值*nIDHelp*为用 (-1)，字符串资源 ID *nIDPrompt*，用于帮助上下文。 有关定义帮助上下文的详细信息，请参阅[技术说明 28](../../mfc/tn028-context-sensitive-help-support.md)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#133](../../mfc/reference/codesnippet/cpp/cstring-formatting-and-message-box-display_4.cpp)]

## <a name="see-also"></a>请参阅

[宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)<br/>
[CStringT 类](../../atl-mfc-shared/reference/cstringt-class.md)
