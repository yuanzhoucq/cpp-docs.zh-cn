---
title: 'Platform:: sizet 值类 |Microsoft 文档'
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/PlatformSizeT::SizeT constructor
dev_langs:
- C++
helpviewer_keywords:
- Platform::SizeT Struct
ms.assetid: 0803612c-8ba1-430c-9b7b-1bebae88608d
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8c69bf34a7965c098f6a656907071e0899b785b4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="platformsizet-value-class"></a>Platform::SizeT 值类
表示对象大小。 SizeT 是无符号数据类型。  
  
## <a name="syntax"></a>语法  
  
```cpp  
public ref class SizeT sealed : ValueType  
```  
  
### <a name="members"></a>成员  
  
|成员|描述|  
|------------|-----------------|  
|[SizeT::SizeT 构造函数](#ctor)|使用指定的值初始化类的新实例。|  
  
### <a name="requirements"></a>要求  
 **支持的最低客户端：** Windows 8  
  
 **支持的最低服务器：** Windows Server 2012  
  
 **命名空间：** Platform  
  
 **元数据：** platform.winmd  

 ## <a name="ctor"></a>  Sizet:: Sizet 构造函数
使用指定值初始化 SizeT 的新实例。  
  
### <a name="syntax"></a>语法  
  
```cpp  
SizeT( uint32 value1 );   SizeT( void* value2 );  
```  
  
### <a name="parameters"></a>参数  
 value1  
 32 位无符号值。  
  
 value2  
 指向 32 位无符号值的指针。  
  
  
## <a name="see-also"></a>请参阅  
 [平台命名空间](../cppcx/platform-namespace-c-cx.md)