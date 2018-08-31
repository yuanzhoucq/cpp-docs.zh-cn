---
title: _com_error::ErrorMessage |Microsoft Docs
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
ms.openlocfilehash: b8dda27c3f1c535f60856bd9d4a3abb9a51a1a32
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43219915"
---
# <a name="comerrorerrormessage"></a>_com_error::ErrorMessage
**Microsoft 专用**  
  
 HRESULT 存储中检索的字符串消息`_com_error`对象。  
  
## <a name="syntax"></a>语法  
  
```  
const TCHAR * ErrorMessage( ) const throw( );  
```  
  
## <a name="return-value"></a>返回值  
 中记录相应的 HRESULT 返回的字符串消息`_com_error`对象。 如果 HRESULT 为映射的 16 位[wCode](../cpp/com-error-wcode.md)，然后一条常规消息"`IDispatch error #<wCode>`"返回。 如果未找到消息，则返回一般消息“`Unknown error #<hresult>`”。 返回的字符串是 Unicode 或多字节字符串，具体取决于 _UNICODE 宏的状态。  
  
## <a name="remarks"></a>备注  
 HRESULT 记录中检索相应的系统消息文本`_com_error`对象。 系统消息文本通过调用 Win32 [FormatMessage](/windows/desktop/api/winbase/nf-winbase-formatmessage)函数。 返回的字符串由 `FormatMessage` API 分配，并在销毁 `_com_error` 对象后释放。  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [_com_error 类](../cpp/com-error-class.md)