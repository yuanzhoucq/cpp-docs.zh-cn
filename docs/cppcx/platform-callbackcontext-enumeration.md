---
title: 'Platform:: callbackcontext 枚举 |Microsoft Docs'
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::CallbackContext
dev_langs:
- C++
helpviewer_keywords:
- Platform::CallbackContext Enumeration
ms.assetid: 60e0c7cb-5d8f-482a-bdca-ca9335ae4899
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4b80fe7749fdb2f91e300cff007c01001edfa557
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2018
ms.locfileid: "43755107"
---
# <a name="platformcallbackcontext-enumeration"></a>Platform::CallbackContext 枚举
指定在其中执行回调函数（事件处理程序）的线程上下文。  
  
## <a name="syntax"></a>语法  
  
```cpp  
enum class CallbackContext {};  
```  
  
### <a name="members"></a>成员  
  
|类型代码|描述|  
|---------------|-----------------|  
|任意|回调函数可以在任何线程上下文上执行。|  
|相同|回调函数只能在启动了异步操作的线程上下文上执行。|  
  
### <a name="requirements"></a>要求  
 **支持的最低客户端：** Windows 8  
  
 **支持的最低服务器：** Windows Server 2012  
  
 **命名空间：** Platform  
  
 **元数据：** platform.winmd