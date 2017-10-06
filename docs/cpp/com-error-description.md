---
title: "_com_error::Description |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _com_error::Description
dev_langs:
- C++
helpviewer_keywords:
- Description method
ms.assetid: 88191e24-4ee8-44a6-8c4c-3758e22e0548
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
ms.openlocfilehash: 0d91f6fded1fa1c4ea4d44cadd0d9285913b5f42
ms.contentlocale: zh-cn
ms.lasthandoff: 09/25/2017

---
# <a name="comerrordescription"></a>_com_error::Description
**Microsoft 专用**  
  
 调用**:: Getdescription**函数。  
  
## <a name="syntax"></a>语法  
  
```  
  
_bstr_t Description( ) const;  
  
```  
  
## <a name="return-value"></a>返回值  
 返回的结果**:: Getdescription**为**IErrorInfo**对象中记录`_com_error`对象。 生成的 `BSTR` 封装在 `_bstr_t` 对象中。 如果没有**IErrorInfo**是记录，它将返回空`_bstr_t`。  
  
## <a name="remarks"></a>备注  
 调用**:: Getdescription**函数并检索**IErrorInfo**中记录`_com_error`对象。 时调用的所有错误**:: Getdescription**方法时将忽略。  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>另请参阅  
 [_com_error 类](../cpp/com-error-class.md)
