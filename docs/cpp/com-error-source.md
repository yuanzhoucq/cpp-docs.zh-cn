---
title: _com_error::Source |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_error::Source
dev_langs:
- C++
helpviewer_keywords:
- Source method [C++]
ms.assetid: 55353741-fabc-4b0c-9787-b5a69bb189f2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f904fa11195c27f8e08856ef391d0ba8adbedece
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2018
ms.locfileid: "37939671"
---
# <a name="comerrorsource"></a>_com_error::Source
**Microsoft 专用**  
  
 调用`IErrorInfo::GetSource`函数。  
  
## <a name="syntax"></a>语法  
  
```  
  
_bstr_t Source() const;  
  
```  
  
## <a name="return-value"></a>返回值  
 返回的结果`IErrorInfo::GetSource`有关`IErrorInfo`对象中记录`_com_error`对象。 生成的 BSTR 封装在 `_bstr_t` 对象中。 如果没有`IErrorInfo`是记录，返回一个空`_bstr_t`。  
  
## <a name="remarks"></a>备注  
 调用时的任何错误`IErrorInfo::GetSource`方法将被忽略。  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [_com_error 类](../cpp/com-error-class.md)