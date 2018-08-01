---
title: _com_error::HelpFile |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_error::HelpFile
dev_langs:
- C++
helpviewer_keywords:
- HelpFile method [C++]
ms.assetid: d2d3a0a1-6b62-4d52-a818-3cfae545a4af
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3afcda41d5dc4ad3cc1fd74ed5449d574946f1e5
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/01/2018
ms.locfileid: "39402037"
---
# <a name="comerrorhelpfile"></a>_com_error::HelpFile
**Microsoft 专用**  
  
 调用`IErrorInfo::GetHelpFile`函数。  
  
## <a name="syntax"></a>语法  
  
```  
_bstr_t HelpFile() const;  
```  
  
## <a name="return-value"></a>返回值  
 返回的结果`IErrorInfo::GetHelpFile`有关`IErrorInfo`对象中记录`_com_error`对象。 生成的 BSTR 封装在 `_bstr_t` 对象中。 如果没有`IErrorInfo`是记录，返回一个空`_bstr_t`。  
  
## <a name="remarks"></a>备注  
 调用时的任何错误`IErrorInfo::GetHelpFile`方法将被忽略。  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [_com_error 类](../cpp/com-error-class.md)