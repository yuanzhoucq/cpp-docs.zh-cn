---
title: Platform::SizeT 值类
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/PlatformSizeT::SizeT constructor
helpviewer_keywords:
- Platform::SizeT Struct
ms.assetid: 0803612c-8ba1-430c-9b7b-1bebae88608d
ms.openlocfilehash: 5add9212dc2655bc37cd357741073f855b009bde
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81322150"
---
# <a name="platformsizet-value-class"></a>Platform::SizeT 值类

表示对象大小。 SizeT 是无符号数据类型。

## <a name="syntax"></a>语法

```cpp
public ref class SizeT sealed : ValueType
```

### <a name="members"></a>成员

|成员|说明|
|------------|-----------------|
|[SizeT::SizeT 构造函数](#ctor)|使用指定的值初始化类的新实例。|

### <a name="requirements"></a>要求

**受支持的最小客户端：** 视窗 8

**受支持的服务器最少：** 视窗服务器 2012

**命名空间：** Platform

**元数据：** 平台.winmd

## <a name="sizetsizet-constructor"></a><a name="ctor"></a>大小T：：SizeT构造函数

使用指定值初始化 SizeT 的新实例。

### <a name="syntax"></a>语法

```cpp
SizeT( uint32 value1 );   SizeT( void* value2 );
```

### <a name="parameters"></a>参数

*值1*<br/>
32 位无符号值。

*值2*<br/>
指向 32 位无符号值的指针。

## <a name="see-also"></a>另请参阅

[Platform 命名空间](../cppcx/platform-namespace-c-cx.md)
