---
title: "_com_error::ErrorInfo |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _com_error::ErrorInfo
dev_langs:
- C++
helpviewer_keywords:
- ErrorInfo method [C++]
ms.assetid: 071b446c-4395-4fb8-bd3d-300a8b25f5cd
caps.latest.revision: 6
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: e80dafb5d1472ec28631b13ab05a0dea0b4de4ba
ms.contentlocale: zh-cn
ms.lasthandoff: 09/25/2017

---
# <a name="comerrorerrorinfo"></a>_com_error::ErrorInfo
**Microsoft 专用**  
  
 检索**IErrorInfo**对象传递给构造函数。  
  
## <a name="syntax"></a>语法  
  
```  
  
IErrorInfo * ErrorInfo( ) const throw( );  
  
```  
  
## <a name="return-value"></a>返回值  
 原始**IErrorInfo**项传递到构造函数。  
  
## <a name="remarks"></a>备注  
 检索封装**IErrorInfo**中项`_com_error`对象，或**NULL**如果没有**IErrorInfo**记录项。 调用方必须调用**版本**在完成返回的对象上使用它。  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>另请参阅  
 [_com_error 类](../cpp/com-error-class.md)
