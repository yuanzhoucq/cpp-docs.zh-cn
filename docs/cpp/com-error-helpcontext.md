---
title: _com_error::HelpContext |Microsoft 文档
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
ms.openlocfilehash: 7123fcf5859ce3fc373b29b4cb3e7b32109b464e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="comerrorhelpcontext"></a>_com_error::HelpContext
**Microsoft 专用**  
  
 调用**ierrorinfo:: Gethelpcontext**函数。  
  
## <a name="syntax"></a>语法  
  
```  
  
DWORD HelpContext( ) const throw( );  
  
```  
  
## <a name="return-value"></a>返回值  
 返回的结果**ierrorinfo:: Gethelpcontext**为**IErrorInfo**对象中记录`_com_error`对象。 如果没有**IErrorInfo**记录对象，它将返回零。  
  
## <a name="remarks"></a>备注  
 时调用的所有错误**ierrorinfo:: Gethelpcontext**方法时将忽略。  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [_com_error 类](../cpp/com-error-class.md)