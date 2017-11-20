---
title: "Platform:: disconnectedexception 类 |Microsoft 文档"
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- VCCORLIB/Platform::DisconnectedException
- VCCORLIB/Platform::DisconnectedException::DisconnectedException
dev_langs: C++
helpviewer_keywords: Platform::DisconnectedException
ms.assetid: c25e0d64-5bff-4c21-88e5-c4ec2776fa7f
caps.latest.revision: "4"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: 0010f039db295f2efc9a8b920d685258a66878d2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="platformdisconnectedexception-class"></a>Platform::DisconnectedException 类
在 COM 代理对象尝试引用不再存在的 COM 服务器时引发  
  
## <a name="syntax"></a>语法  
  
```  
public ref class DisconnectedException : COMException,    IException,    IPrintable,    IEquatable  
```  
  
### <a name="remarks"></a>备注  
 当类 A 引用另一个单独进程中的类（类 B）时，类 A 需要一个代理对象与承载类 B 的进程外 COM 服务器进行通信。有时该服务器可以在类 A 不知情的情况下离开内存。 在该情况下，将引发 RPC_E_DISCONNECTED 异常并且它转换为 Platform::DisconnectedException。 它发生的一种情况是，当事件源调用传递到它的委托，但该委托已在订阅该事件后的某个时点被销毁时。 当发生这种情况时，该事件源将移除来自其调用列表的委托。  
  
 有关更多信息，请参见 [COMException](../cppcx/platform-comexception-class.md) 类。  
  
### <a name="requirements"></a>要求  
 **支持的最低客户端：** Windows 8  
  
 **支持的最低服务器：** Windows Server 2012  
  
 **命名空间：** Platform  
  
 **元数据：** platform.winmd  
  
## <a name="see-also"></a>另请参阅  
 [Platform::COMException 类](../cppcx/platform-comexception-class.md)