---
title: "_com_error::Error |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _com_error::Error
- Error
dev_langs: C++
helpviewer_keywords: Error method [C++]
ms.assetid: b53a15fd-198e-4276-afcd-13439c4807f7
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 010d1b2e10d1435855c35929516ff0e7f3fd8d4e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="comerrorerror"></a>_com_error::Error
**Microsoft 专用**  
  
 检索传递给构造函数的 `HRESULT`。  
  
## <a name="syntax"></a>语法  
  
```  
  
HRESULT Error( ) const throw( );  
  
```  
  
## <a name="return-value"></a>返回值  
 已传入构造函数的原始 `HRESULT` 项。  
  
## <a name="remarks"></a>备注  
 检索 `HRESULT` 对象中封装的 `_com_error` 项。  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>另请参阅  
 [_com_error 类](../cpp/com-error-class.md)