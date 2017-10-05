---
title: "_com_error::operator = |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _com_error::operator=
- _com_error.operator=
dev_langs:
- C++
helpviewer_keywords:
- operator= _com_error objects
- = operator, with specific Visual C++ objects
- operator = _com_error objects
ms.assetid: b9cc4094-d055-450c-b45a-0a95317488f8
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
ms.openlocfilehash: ddbd09e7783818cb5d2bc72941c8f9e0472e7a3c
ms.contentlocale: zh-cn
ms.lasthandoff: 09/25/2017

---
# <a name="comerroroperator-"></a>_com_error::operator =
**Microsoft 专用**  
  
 将现有 `_com_error` 对象赋给另一个对象。  
  
## <a name="syntax"></a>语法  
  
```  
  
      _com_error& operator = (  
   const _com_error& that   
) throw ( );  
```  
  
#### <a name="parameters"></a>参数  
 `that`  
 一个 `_com_error` 对象。  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>另请参阅  
 [_com_error 类](../cpp/com-error-class.md)
