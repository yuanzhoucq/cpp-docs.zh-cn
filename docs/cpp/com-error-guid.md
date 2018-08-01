---
title: _com_error::GUID |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_error::GUID
dev_langs:
- C++
helpviewer_keywords:
- GUID method [C++]
ms.assetid: e84c2c23-d02e-48f8-b776-9bd6937296d2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c592607732eb5558ce74edb7b71adbc023b2ae52
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/01/2018
ms.locfileid: "39402278"
---
# <a name="comerrorguid"></a>_com_error::GUID
**Microsoft 专用**  
  
 调用`IErrorInfo::GetGUID`函数。  
  
## <a name="syntax"></a>语法  
  
```  
GUID GUID( ) const throw( );  
```  
  
## <a name="return-value"></a>返回值  
 返回的结果`IErrorInfo::GetGUID`有关`IErrorInfo`对象中记录`_com_error`对象。 如果没有`IErrorInfo`记录对象时，它将返回`GUID_NULL`。  
  
## <a name="remarks"></a>备注  
 调用时的任何错误`IErrorInfo::GetGUID`方法将被忽略。  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [_com_error 类](../cpp/com-error-class.md)