---
title: "Platform:: sizet 值类 |Microsoft 文档"
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: VCCORLIB/PlatformSizeT::SizeT constructor
dev_langs: C++
helpviewer_keywords: Platform::SizeT Struct
ms.assetid: 0803612c-8ba1-430c-9b7b-1bebae88608d
caps.latest.revision: "4"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: bf47d911dc348b23e371175cf46fc6d677ce9f36
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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
  
### <a name="requirements"></a>惠?  
 **支持的最低客户端：** Windows 8  
  
 **支持的最低服务器：** Windows Server 2012  
  
 **命名空间：** Platform  
  
 **元数据：** platform.winmd  

 ## <a name="ctor"></a>Sizet:: Sizet 构造函数
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