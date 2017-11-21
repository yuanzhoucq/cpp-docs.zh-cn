---
title: "_com_error::Description |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: _com_error::Description
dev_langs: C++
helpviewer_keywords: Description method [C++]
ms.assetid: 88191e24-4ee8-44a6-8c4c-3758e22e0548
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c4bf868fd548cc7e0c72559f3754d7e1a035cfa5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
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