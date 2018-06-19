---
title: _com_error::Source |Microsoft 文档
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
ms.openlocfilehash: a33834df20606e8380e6a328a41435522185ac70
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32412340"
---
# <a name="comerrorsource"></a>_com_error::Source
**Microsoft 专用**  
  
 调用**ierrorinfo:: Getsource**函数。  
  
## <a name="syntax"></a>语法  
  
```  
  
_bstr_t Source() const;  
  
```  
  
## <a name="return-value"></a>返回值  
 返回的结果**ierrorinfo:: Getsource**为**IErrorInfo**对象中记录`_com_error`对象。 生成的 BSTR 封装在 `_bstr_t` 对象中。 如果没有**IErrorInfo**是记录，它将返回空`_bstr_t`。  
  
## <a name="remarks"></a>备注  
 时调用的所有错误**ierrorinfo:: Getsource**方法时将忽略。  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [_com_error 类](../cpp/com-error-class.md)