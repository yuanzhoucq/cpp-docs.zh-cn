---
title: "Platform:: stathreadattribute 类 |Microsoft 文档"
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Platform
- COLLECTION/Platform::Platform::STAThreadAttribute constructor 1
- COLLECTION/Platform::Platform::STAThreadAttribute::Equals
- COLLECTION/Platform::Platform::STAThreadAttribute::GetHashCode
- COLLECTION/Platform::Platform::STAThreadAttribute::ToString
dev_langs:
- C++
helpviewer_keywords:
- Platform::STAThreadAttribute Class
ms.assetid: f97960fc-e673-4d9e-910a-54c8415411c4
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: db66ba0775ad3b38be1b43fd5781be611ca2f333
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="platformstathreadattribute-class"></a>Platform::STAThreadAttribute 类
指示应用程序的线程模型是单线程单元 (STA)。  
  
## <a name="syntax"></a>语法  
  
```  
public ref class STAThreadAttribute sealed : Attribute  
```  
  
### <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[STAThreadAttribute 构造函数 1](#ctor)|初始化类的新实例。|  
  
### <a name="public-methods"></a>公共方法  
 STAThreadAttribute 属性继承自[platform:: object 类](../cppcx/platform-object-class.md)。 STAThreadAttribute 还会重载或具有以下成员：  
  
|name|描述|  
|----------|-----------------|  
|[STAThreadAttribute::Equals](#equals)|确定指定的对象是否等于当前对象。|  
|[STAThreadAttribute::GetHashCode](#gethashcode)|返回此实例的哈希代码。|  
|[STAThreadAttribute::ToString](#tostring)|返回表示当前对象的字符串。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `Platform`  
  
### <a name="requirements"></a>惠?  
 **标头：** collection.h  
  
 **命名空间：** Platform  



## <a name="ctor"></a> STAThreadAttribute constructor
初始化 STAThreadAttribute 类的新实例。  
  
### <a name="syntax"></a>语法  
  
```cpp  
public:STAThreadAttribute()  
```  
  


## <a name="equals"></a> STAThreadAttribute::Equals
确定指定的对象是否等于当前对象。  
  
### <a name="syntax"></a>语法  
  
```cpp  
public:virtual override bool Equals(  Object^ obj)  
```  
  
### <a name="parameters"></a>参数  
 obj  
 要比较的对象。  
  
### <a name="return-value"></a>返回值  
 如果对象相等，则为 `true`；否则为 `false`。  
  


## <a name="gethashcode"></a> STAThreadAttribute::GetHashCode
返回此实例的哈希代码。  
  
### <a name="syntax"></a>语法  
  
```cpp  
public:int GetHashCode()  
```  
  
### <a name="return-value"></a>返回值  
 此实例的哈希代码。  
  


## <a name="tostring"></a> STAThreadAttribute::ToString
返回表示当前对象的字符串。  
  
### <a name="syntax"></a>语法  
  
```cpp  
public:String^ ToString()  
```  
  
### <a name="return-value"></a>返回值  
 表示当前对象的字符串。  
  

  
## <a name="see-also"></a>请参阅  
 [平台 Namespace](platform-namespace-c-cx.md)