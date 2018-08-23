---
title: RoInitializeWrapper 类 |Microsoft Docs
ms.custom: ''
ms.date: 05/20/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::RoInitializeWrapper
dev_langs:
- C++
ms.assetid: 4055fbe0-63a7-4c06-b5a0-414fda5640e5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6f5c47ac34d8b159e75acf672ba57ca8c1ebac1e
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42592824"
---
# <a name="roinitializewrapper-class"></a>RoInitializeWrapper 类

初始化 Windows 运行时。

## <a name="syntax"></a>语法

```cpp
class RoInitializeWrapper
```

## <a name="remarks"></a>备注

**RoInitializeWrapper**是一种便于初始化 Windows 运行时并返回一个 HRESULT，指示操作是否成功。 因为类析构函数调用`::Windows::Foundation::Uninitialize`的实例**RoInitializeWrapper**必须在全局或顶级范围内声明。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[RoInitializeWrapper::RoInitializeWrapper 构造函数](../windows/roinitializewrapper-roinitializewrapper-constructor.md)|初始化的新实例**RoInitializeWrapper**类。|
|[RoInitializeWrapper::~RoInitializeWrapper 析构函数](../windows/roinitializewrapper-tilde-roinitializewrapper-destructor.md)|销毁的当前实例**RoInitializeWrapper**类。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[RoInitializeWrapper::HRESULT() 运算符](../windows/roinitializewrapper-hresult-parens-operator.md)|检索生成的 HRESULT **RoInitializeWrapper**构造函数。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`RoInitializeWrapper`

## <a name="requirements"></a>要求

**标头：** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers

## <a name="see-also"></a>请参阅

[Microsoft::WRL::Wrappers 命名空间](../windows/microsoft-wrl-wrappers-namespace.md)