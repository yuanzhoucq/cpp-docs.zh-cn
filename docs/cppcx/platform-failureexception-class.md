---
title: 'Platform:: failureexception 类 |Microsoft 文档'
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::FailureException::FailureException
- VCCORLIB/Platform::FailureException
dev_langs:
- C++
helpviewer_keywords:
- Platform::FailureException
ms.assetid: 1729cd07-bfc2-448e-9db5-185d5cbf5b81
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1094810663ce0a0abf8234af386d7a8427472ced
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33088136"
---
# <a name="platformfailureexception-class"></a>Platform::FailureException 类
操作失败时引发。 它是 E_FAIL HRESULT 的等效项。  
  
## <a name="syntax"></a>语法  
  
```cpp  
public ref class FailureException : COMException,    IException,    IPrintable,    IEquatable  
```  
  
### <a name="remarks"></a>备注  
 有关更多信息，请参见 [COMException](../cppcx/platform-comexception-class.md) 类。  
  
### <a name="requirements"></a>要求  
 **支持的最低客户端：** Windows 8  
  
 **支持的最低服务器：** Windows Server 2012  
  
 **命名空间：** Platform  
  
 **元数据：** platform.winmd  
  
## <a name="see-also"></a>请参阅  
 [Platform::COMException 类](../cppcx/platform-comexception-class.md)