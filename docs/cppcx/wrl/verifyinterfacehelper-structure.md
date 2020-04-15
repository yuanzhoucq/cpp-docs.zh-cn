---
title: VerifyInterfaceHelper 结构
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::VerifyInterfaceHelper
- implements/Microsoft::WRL::Details::VerifyInterfaceHelper::Verify
helpviewer_keywords:
- Microsoft::WRL::Details::VerifyInterfaceHelper structure
- Microsoft::WRL::Details::VerifyInterfaceHelper::Verify method
ms.assetid: ea95b641-199a-4fdf-964b-186b40cb3ba7
ms.openlocfilehash: 09c2cc7e08e2dc0e8df42c64d285c37627c5925a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374238"
---
# <a name="verifyinterfacehelper-structure"></a>VerifyInterfaceHelper 结构

支持 Windows 运行时C++模板库基础结构，并且不打算直接从代码中使用。

## <a name="syntax"></a>语法

```cpp
template <bool isWinRTInterface, typename I>
struct VerifyInterfaceHelper;

template <typename I>
struct VerifyInterfaceHelper<false, I>;
```

### <a name="parameters"></a>参数

*Ⅰ*<br/>
要验证的接口。

*是WinRT接口*

## <a name="remarks"></a>备注

验证模板参数指定的接口是否满足某些要求。

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

名称                                            | 说明
----------------------------------------------- | ---------------------------------------------------------------------------------------------------
[VerifyInterfaceHelper::Verify 方法](#verify) | 验证当前模板参数指定的接口是否满足某些要求。

## <a name="inheritance-hierarchy"></a>继承层次结构

`VerifyInterfaceHelper`

## <a name="requirements"></a>要求

**标题：** 实现.h

**命名空间：** 微软：：WRL：:D

## <a name="verifyinterfacehelperverify"></a><a name="verify"></a>验证接口帮助程序：：验证

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
static void Verify();
```

### <a name="remarks"></a>备注

验证当前模板参数指定的接口是否满足某些要求。
