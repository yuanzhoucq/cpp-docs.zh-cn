---
title: 'Platform:: sizet 值类 |Microsoft Docs'
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f60349203ce55a927ffac3d095988e5198bedd87
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42601916"
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