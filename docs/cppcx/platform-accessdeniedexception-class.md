---
title: 'Platform:: accessdeniedexception 类 |Microsoft Docs'
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::AccessDeniedException
- VCCORLIB/Platform::AccessDeniedException::AccessDeniedException
dev_langs:
- C++
helpviewer_keywords:
- Platform::AccessDeniedException
ms.assetid: 6ae2155b-7b16-4587-8d2d-da05eab4c7e9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 808de08163f0f94e4c3d0064fced7cb81f83c931
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2018
ms.locfileid: "43767925"
---
# <a name="platformaccessdeniedexception-class"></a>Platform::AccessDeniedException 类
被拒绝访问资源或功能时引发。  
  
## <a name="syntax"></a>语法  
  
```cpp  
public ref class AccessDeniedException : COMException,    IException,    IPrintable,   IEquatable  
```  
  
### <a name="remarks"></a>备注  
 如果碰到此异常，请确保已请求适当的功能，并在您的应用程序的包清单中做了必需的声明。 有关更多信息，请参见 [COMException](../cppcx/platform-comexception-class.md) 类。  
  
### <a name="requirements"></a>要求  
 **支持的最低客户端：** Windows 8  
  
 **支持的最低服务器：** Windows Server 2012  
  
 **命名空间：** Platform  
  
 **元数据：** platform.winmd  
  
## <a name="see-also"></a>请参阅  
 [Platform::COMException 类](../cppcx/platform-comexception-class.md)