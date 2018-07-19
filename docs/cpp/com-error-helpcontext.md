---
title: _com_error::HelpContext |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_error::HelpContext
dev_langs:
- C++
helpviewer_keywords:
- HelpContext method [C++]
ms.assetid: 160d6443-9b68-4cf5-a540-50da951a5b2b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e800bd3100fa0199534f3e9bdf6646aa0ffc6860
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2018
ms.locfileid: "37940893"
---
# <a name="comerrorhelpcontext"></a>_com_error::HelpContext
**Microsoft 专用**  
  
 调用`IErrorInfo::GetHelpContext`函数。  
  
## <a name="syntax"></a>语法  
  
```  
  
DWORD HelpContext( ) const throw( );  
  
```  
  
## <a name="return-value"></a>返回值  
 返回的结果`IErrorInfo::GetHelpContext`有关`IErrorInfo`对象中记录`_com_error`对象。 如果没有`IErrorInfo`记录对象，它将返回零。  
  
## <a name="remarks"></a>备注  
 调用时的任何错误`IErrorInfo::GetHelpContext`方法将被忽略。  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [_com_error 类](../cpp/com-error-class.md)