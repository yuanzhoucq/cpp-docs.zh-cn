---
title: 'Platform:: wrongthreadexception 类 |Microsoft 文档'
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::WrongThreadException
- VCCORLIB/Platform::WrongThreadException::WrongThreadException
dev_langs:
- C++
helpviewer_keywords:
- Platform::WrongThreadException
ms.assetid: c193f97e-0392-4535-a4c4-0711e4e4a836
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f01b52470f5c70c588c7905a2c46f7cae9b26d06
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33088253"
---
# <a name="platformwrongthreadexception-class"></a>Platform::WrongThreadException 类
当线程通过不属于该线程单元的代理对象的接口指针调用时引发。  
  
## <a name="syntax"></a>语法  
  
```cpp  
public ref class WrongThreadException : COMException,    IException,    IPrintable,    IEquatable  
```  
  
### <a name="remarks"></a>备注  
 有关更多信息，请参见 [COMException](../cppcx/platform-comexception-class.md)。  
  
### <a name="requirements"></a>要求  
 **支持的最低客户端：** Windows 8  
  
 **支持的最低服务器：** Windows Server 2012  
  
 **命名空间：** Platform  
  
 **元数据：** platform.winmd  
  
## <a name="see-also"></a>请参阅  
 [Platform::COMException 类](../cppcx/platform-comexception-class.md)