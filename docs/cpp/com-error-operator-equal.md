---
title: "_com_error::operator = |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: _com_error::operator=
dev_langs: C++
helpviewer_keywords:
- operator= _com_error objects
- = operator [C++], with specific Visual C++ objects
- operator = _com_error objects
ms.assetid: b9cc4094-d055-450c-b45a-0a95317488f8
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b0f1cee441130c7c5b877a345e742e6e24c380f9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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
  
## <a name="see-also"></a>请参阅  
 [_com_error 类](../cpp/com-error-class.md)