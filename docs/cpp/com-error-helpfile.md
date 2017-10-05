---
title: "_com_error::HelpFile |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- HelpFile
- _com_error::HelpFile
- _com_error.HelpFile
dev_langs:
- C++
helpviewer_keywords:
- HelpFile method
ms.assetid: d2d3a0a1-6b62-4d52-a818-3cfae545a4af
caps.latest.revision: 6
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
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 7e1e9ec8c7d6684bb7b244fd9ba6773b6f1460e1
ms.contentlocale: zh-cn
ms.lasthandoff: 09/25/2017

---
# <a name="comerrorhelpfile"></a>_com_error::HelpFile
**Microsoft 专用**  
  
 调用**:: Gethelpfile**函数。  
  
## <a name="syntax"></a>语法  
  
```  
  
_bstr_t HelpFile() const;  
  
```  
  
## <a name="return-value"></a>返回值  
 返回的结果**:: Gethelpfile**为**IErrorInfo**对象中记录`_com_error`对象。 生成的 BSTR 封装在 `_bstr_t` 对象中。 如果没有**IErrorInfo**是记录，它将返回空`_bstr_t`。  
  
## <a name="remarks"></a>备注  
 时调用的所有错误**:: Gethelpfile**方法时将忽略。  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>另请参阅  
 [_com_error 类](../cpp/com-error-class.md)
