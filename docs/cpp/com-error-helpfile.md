---
title: _com_error::HelpFile |Microsoft 文档
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
ms.openlocfilehash: a1f02238d228b5de4302812bacf4f9ad5cf1300c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32409782"
---
# <a name="comerrorhelpfile"></a>_com_error::HelpFile
**Microsoft 专用**  
  
 调用 **:: Gethelpfile**函数。  
  
## <a name="syntax"></a>语法  
  
```  
  
_bstr_t HelpFile() const;  
  
```  
  
## <a name="return-value"></a>返回值  
 返回的结果 **:: Gethelpfile**为**IErrorInfo**对象中记录`_com_error`对象。 生成的 BSTR 封装在 `_bstr_t` 对象中。 如果没有**IErrorInfo**是记录，它将返回空`_bstr_t`。  
  
## <a name="remarks"></a>备注  
 时调用的所有错误 **:: Gethelpfile**方法时将忽略。  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [_com_error 类](../cpp/com-error-class.md)