---
title: "_com_error::HelpFile |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: _com_error::HelpFile
dev_langs: C++
helpviewer_keywords: HelpFile method [C++]
ms.assetid: d2d3a0a1-6b62-4d52-a818-3cfae545a4af
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: cac4eda3b84243c09043d8f57a04d3cc5fb8a662
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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
  
## <a name="see-also"></a>请参阅  
 [_com_error 类](../cpp/com-error-class.md)