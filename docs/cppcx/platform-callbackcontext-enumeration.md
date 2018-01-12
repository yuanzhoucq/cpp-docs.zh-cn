---
title: "Platform:: callbackcontext 枚举 |Microsoft 文档"
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: VCCORLIB/Platform::CallbackContext
dev_langs: C++
helpviewer_keywords: Platform::CallbackContext Enumeration
ms.assetid: 60e0c7cb-5d8f-482a-bdca-ca9335ae4899
caps.latest.revision: "3"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ede3cfecadbe87caf5182e0d3df9c25a481f3079
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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
  
### <a name="requirements"></a>惠?  
 **支持的最低客户端：** Windows 8  
  
 **支持的最低服务器：** Windows Server 2012  
  
 **命名空间：** Platform  
  
 **元数据：** platform.winmd