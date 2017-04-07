---
title: "CString 格式设置和消息框显示 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.macros.strings
dev_langs:
- C++
helpviewer_keywords:
- CString objects, formatting and message boxes
ms.assetid: d1068cf4-9cc5-4952-b9e7-d612c53cbc28
caps.latest.revision: 14
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
ms.sourcegitcommit: 3d045736f9a54d344c67e3f7408198e65a0bc95f
ms.openlocfilehash: 356562dc61971aa7a74ce9e9be94fc34af58f6f9
ms.lasthandoff: 03/29/2017

---
# <a name="cstring-formatting-and-message-box-display"></a>CString 格式设置和消息框显示
提供的许多功能进行格式化和分析`CString`对象。 每当你操作时，可以使用这些函数`CString`对象，但它们都将出现在消息框文本的字符串设置格式特别有用。  
  
 此组的函数还包括用于显示一个消息框的全局例程。  
  
### <a name="cstring-functions"></a>CString 函数  
  
|||  
|-|-|  
|[AfxExtractSubString](#afxextractsubstring)|提取子字符串从给定的源字符串的单个字符分隔。|  
|[AfxFormatString1](#afxformatstring1)|替换字符串中的格式字符"%1"的给定的字符串包含在字符串表中。|  
|[AfxFormatString2](#afxformatstring2)|替换两个字符串的格式字符"%1"和"%2"在字符串中包含字符串表中。|  
|[AfxMessageBox](#afxmessagebox)|显示消息框。|  
  
### <a name="requirements"></a>要求  
  **标头**afxwin.h  
  
##  <a name="afxextractsubstring"></a>AfxExtractSubString  
 此全局函数可用来从给定的源字符串中提取子字符串。  
  
```   
BOOL AFXAPI AfxExtractSubString (
    CString& rString,  
    LPCTSTR lpszFullString,  
    int iSubString,  
    TCHAR chSep  = '\n'); 
```  
  
### <a name="parameters"></a>参数  
 *rString*  
 -   引用[CString](../../atl-mfc-shared/using-cstring.md)将接收单个子字符串的对象。  
  
 *lpszFullString*  
 -   包含要提取的字符串的完整文本的字符串。  
  
 *iSubString*  
 -   要从提取的子字符串的从零开始索引*lpszFullString*。  
  
 *chSep*  
 -   用于分隔子字符串的分隔符字符。  
  
### <a name="return-value"></a>返回值  
 **TRUE**如果函数成功提取的子字符串在提供的索引; 否则为**FALSE**。  
  
### <a name="remarks"></a>备注  
 此函数可用于从源字符串提取的多个子时已知的单个字符用于分隔每个子字符串。 此函数将搜索从开始处`lpszFullString`参数每次调用时。  
  
 此函数将返回 FALSE，如果任一`lpszFullString`设置为**NULL**或函数到达末尾`lpszFullString`没有找到`iSubString`+ 1 个指定的分隔符字符。 `rString`如果参数将不从其原始值会修改`lpszFullString`已设置为**NULL**; 否则为`rString`参数设置为空字符串，如果指定的索引，无法提取子字符串。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_Utilities # 48](../../mfc/codesnippet/cpp/cstring-formatting-and-message-box-display_1.cpp)]  
  
### <a name="requirements"></a>要求  
  **标头**afxwin.h  
  
##  <a name="afxformatstring1"></a>AfxFormatString1  
 将 `lpsz1` 指向的字符串替换为 `nIDS` 标识的模板字符串资源中的字符“%1”的任何实例。  
  
```  
void  AfxFormatString1(
    CString& rString,  
    UINT nIDS,  
    LPCTSTR lpsz1); 
```  
  
### <a name="parameters"></a>参数  
 `rString`  
 对在执行替换后将包含生成字符串的 `CString` 对象的引用。  
  
 `nIDS`  
 将对其执行替换的模板字符串的资源 ID。  
  
 `lpsz1`  
 将替换模板字符串中的格式字符串“%1”的字符串。  
  
### <a name="remarks"></a>备注  
 新构成的字符串存储在 `rString` 中。 例如，如果字符串表中的字符串为“未找到文件 %1”，并且 `lpsz1` 等效于“C:\MYFILE.TXT”，则 `rString` 将包含字符串“未找到文件 C:\MYFILE.TXT”。 此函数对为发送到消息框和其他窗口的字符串设置格式很有用。  
  
 如果格式字符“%1”多次出现在字符串中，则将执行多次替换。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_Utilities # 25](../../mfc/codesnippet/cpp/cstring-formatting-and-message-box-display_2.cpp)]  
  
### <a name="requirements"></a>要求  
  **标头**afxwin.h  
  
##  <a name="afxformatstring2"></a>AfxFormatString2  
 替换字符串的指向`lpsz1`字符"%1"，并通过指向的任何的字符串实例`lpsz2`所标识的模板字符串资源中的字符"%2"的任何实例`nIDS`。  
  
```   
void AfxFormatString2(
    CString& rString,  
    UINT nIDS,  
    LPCTSTR lpsz1,  
    LPCTSTR lpsz2); 
```  
  
### <a name="parameters"></a>参数  
 `rString`  
 对引用`CString`执行替换后将包含生成的字符串。  
  
 `nIDS`  
 将对其执行替换的模板字符串的字符串表 ID。  
  
 `lpsz1`  
 将替换模板字符串中的格式字符串“%1”的字符串。  
  
 `lpsz2`  
 将替换格式的字符串的模板字符串中字符"%2"。  
  
### <a name="remarks"></a>备注  
 新构成的字符串存储在 `rString` 中。 例如，如果字符串表中的字符串为"文件目录 %2 中找不到 %1"，`lpsz1`指向"MYFILE。TXT"、 和`lpsz2`然后指向"C:\MYDIR"`rString`将包含字符串"File MYFILE。TXT 目录 C:\MYDIR 中未找到"  
  
 如果格式字符"%1"或"%2"多次出现在字符串中，将进行多个替换项。 它们无需按数字顺序。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_Utilities # 26](../../mfc/codesnippet/cpp/cstring-formatting-and-message-box-display_3.cpp)]  
  
### <a name="requirements"></a>要求  
  **标头**afxwin.h  
  
##  <a name="afxmessagebox"></a>AfxMessageBox  
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
 `lpszText`  
 指向`CString`对象或包含在消息框中显示的消息的以 null 结尾的字符串。  
  
 `nType`  
 在消息框样式。 应用任何[消息框样式](../../mfc/reference/message-box-styles.md)在框中。  
  
 `nIDHelp`  
 消息; 的帮助上下文 ID0 指示将使用应用程序的默认帮助上下文。  
  
 `nIDPrompt`  
 用来引用字符串表中的字符串的唯一 ID。  
  
### <a name="return-value"></a>返回值  
 如果没有足够的内存来显示消息框中; 则为零否则，返回以下值之一︰  
  
- **IDABORT**选择中止按钮。  
  
- **IDCANCEL**选择了取消按钮。  
  
- **IDIGNORE**已选择忽略按钮。  
  
- **IDNO**选择否按钮。  
  
- **IDOK**选择确定按钮。  
  
- **IDRETRY**选择重试按钮。  
  
- **IDYES**选择是按钮。  
  
 如果一个消息框具有取消按钮， **IDCANCEL**将返回值，如果按 ESC 键，或者选择取消按钮。 如果消息框没有取消按钮，按 ESC 键不起作用。  
  
 函数[AfxFormatString1](#afxformatstring1)和[AfxFormatString2](#afxformatstring2)中设置文本框中显示一个消息框文本的格式会很有用。  
  
### <a name="remarks"></a>备注  
 第一种形式的此重载函数显示的文本字符串指向`lpszText`消息框并使用`nIDHelp`来描述帮助上下文。 帮助上下文用于当用户按下的帮助按钮 (通常 F1) 跳转到关联的帮助主题。  
  
 函数的第二种形式的字符串资源使用 ID`nIDPrompt`在消息框中显示一条消息。 关联的帮助页找到的值通过`nIDHelp`。 如果默认值的`nIDHelp`为使用 (-1)，字符串资源 ID， `nIDPrompt`，用于帮助上下文。 有关定义帮助上下文的详细信息，请参阅[技术注意 28](../../mfc/tn028-context-sensitive-help-support.md)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing # 133](../../mfc/reference/codesnippet/cpp/cstring-formatting-and-message-box-display_4.cpp)]  
  
## <a name="see-also"></a>另请参阅  
 [宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)   
 [CStringT 类](../../atl-mfc-shared/reference/cstringt-class.md)

