---
title: _com_error::ErrorMessage |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_error::ErrorMessage
dev_langs:
- C++
helpviewer_keywords:
- ErrorMessage method [C++]
ms.assetid: e47335b6-01af-4975-a841-121597479eb7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c16b8bb6859cd65b534d804764257b901050995b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="comerrorerrormessage"></a>_com_error::ErrorMessage
**Microsoft 专用**  
  
 检索存储在 `HRESULT` 对象中的 `_com_error` 的字符串消息。  
  
## <a name="syntax"></a>语法  
  
```  
  
const TCHAR * ErrorMessage( ) const throw( );  
  
```  
  
## <a name="return-value"></a>返回值  
 返回在 `HRESULT` 对象中记录的 `_com_error` 的字符串消息。 如果`HRESULT`是映射的 16 位[wCode](../cpp/com-error-wcode.md)，然后一条常规消息"`IDispatch error #<wCode>`"返回。 如果未找到消息，则返回一般消息“`Unknown error #<hresult>`”。 返回的字符串是 Unicode 或多字节字符串，具体取决于的状态 **_UNICODE**宏。  
  
## <a name="remarks"></a>备注  
 检索在 `HRESULT` 对象中记录的 `_com_error` 的对应系统消息文本。 系统消息文本通过调用 Win32 获取[FormatMessage](http://msdn.microsoft.com/library/windows/desktop/ms679351)函数。 返回的字符串由 `FormatMessage` API 分配，并在销毁 `_com_error` 对象后释放。  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [_com_error 类](../cpp/com-error-class.md)