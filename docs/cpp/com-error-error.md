---
title: _com_error::Error |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_error::Error
- Error
dev_langs:
- C++
helpviewer_keywords:
- Error method [C++]
ms.assetid: b53a15fd-198e-4276-afcd-13439c4807f7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6a7ddaefcf3bd46bf40b03c03d2d1fb00cf8fbbb
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/01/2018
ms.locfileid: "39408422"
---
# <a name="comerrorerror"></a>_com_error::Error
**Microsoft 专用**  
  
 检索传递给构造函数的 HRESULT。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT Error( ) const throw( );  
```  
  
## <a name="return-value"></a>返回值  
 原始 HRESULT 项传递到构造函数。  
  
## <a name="remarks"></a>备注  
 检索中的封装的 HRESULT 项`_com_error`对象。  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [_com_error 类](../cpp/com-error-class.md)