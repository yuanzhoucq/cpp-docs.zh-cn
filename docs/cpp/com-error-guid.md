---
title: _com_error::GUID |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_error::GUID
dev_langs:
- C++
helpviewer_keywords:
- GUID method [C++]
ms.assetid: e84c2c23-d02e-48f8-b776-9bd6937296d2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ee1952e50251cfac7563357c7626ab8603589e4d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32409673"
---
# <a name="comerrorguid"></a>_com_error::GUID
**Microsoft 专用**  
  
 调用 **:: Getguid**函数。  
  
## <a name="syntax"></a>语法  
  
```  
  
GUID GUID( ) const throw( );  
  
```  
  
## <a name="return-value"></a>返回值  
 返回的结果 **:: Getguid**为**IErrorInfo**对象中记录`_com_error`对象。 如果没有**IErrorInfo**记录对象，它将返回`GUID_NULL`。  
  
## <a name="remarks"></a>备注  
 时调用的所有错误 **:: Getguid**方法时将忽略。  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [_com_error 类](../cpp/com-error-class.md)