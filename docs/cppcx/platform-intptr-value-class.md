---
title: 'Platform:: intptr 值类 |Microsoft 文档'
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/PlatformIntPtr::IntPtr
- VCCORLIB/PlatformIntPtr::op_explicit Operator
- VCCORLIB/PlatformIntPtr::ToInt32
dev_langs:
- C++
helpviewer_keywords:
- Platform::IntPtr Struct
ms.assetid: 6c0326e8-edfd-4e53-a963-240b845dcde8
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b54facc94be3f43b500e38371e0eba9e00d130a4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33088149"
---
# <a name="platformintptr-value-class"></a>Platform::IntPtr 值类
表示一个签名指针或句柄，并且其大小特定于平台（32 位或 64 位）。  
  
## <a name="syntax"></a>语法  
  
```cpp  
public value struct IntPtr  
```  
  
### <a name="members"></a>成员  
 IntPtr 具有下列成员：  
  
|成员|描述|  
|------------|-----------------|  
|[IntPtr::IntPtr](#ctor)|初始化 IntPtr 的一个新实例。|  
|[IntPtr::op_explicit 运算符](#op-explicit)|将指定参数转换为 IntPtr 或指向 IntPtr 值的指针。|  
|[IntPtr::ToInt32](#toint32)|将当前 IntPtr 转换为 32 位整数。|  
  
### <a name="requirements"></a>要求  
 **支持的最低客户端：** Windows 8  
  
 **支持的最低服务器：** Windows Server 2012  
  
 **命名空间：** Platform  
  
 **元数据：** platform.winmd  

## <a name="ctor"> </a> IntPtr::IntPtr 构造函数
使用指定值初始化 IntPtr 的新实例。  
  
### <a name="syntax"></a>语法  
  
```cpp  
IntPtr( __int64 handle-or-pointer );   IntPtr( void* value );   IntPtr( int 32-bit_value );  
```  
  
### <a name="parameters"></a>参数  
 值  
 一个 64 位句柄或指针，或指向 64 位值或可被转换为 64 位值的 32 位值的指针。  
  


## <a name="op-explicit"> </a> IntPtr::op_explicit 运算符
将指定参数转换为 IntPtr 或指向 IntPtr 值的指针。  
  
### <a name="syntax"></a>语法  
  
```cpp  
static IntPtr::operator IntPtr( void* value1);   static IntPtr::operator IntPtr( int value2);   static IntPtr::operator void*( IntPtr value3 );  
```  
  
### <a name="parameters"></a>参数  
 value1  
 指向句柄或 IntPtr 的指针。  
  
 value2  
 可以转换为 IntPtr 的 32 位整数。  
  
 value3  
 一个 IntPtr。  
  
### <a name="return-value"></a>返回值  
 第一个和第二个运算符返回 IntPtr。 第三个运算符返回指向当前 IntPtr 表示的值的指针。  
  


## <a name="toint32"> </a> Intptr:: Toint32 方法
将当前 IntPtr 值转换为 32 位整数。  
  
### <a name="syntax"></a>语法  
  
```cpp  
int32 IntPtr::ToInt32();  
```  
  
### <a name="return-value"></a>返回值  
 32 位整数。  
  
  
## <a name="see-also"></a>请参阅  
 [平台命名空间](../cppcx/platform-namespace-c-cx.md)