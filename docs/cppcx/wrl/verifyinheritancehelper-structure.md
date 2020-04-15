---
title: VerifyInheritanceHelper 结构
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::VerifyInheritanceHelper
- implements/Microsoft::WRL::Details::VerifyInheritanceHelper::Verify
helpviewer_keywords:
- Microsoft::WRL::Details::VerifyInheritanceHelper structure
- Microsoft::WRL::Details::VerifyInheritanceHelper::Verify method
ms.assetid: 8a48a702-0f71-4807-935b-8311f0a7a8b6
ms.openlocfilehash: 3650cfb70ffc12572b3965534eff4e1f2ecb2cf5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374230"
---
# <a name="verifyinheritancehelper-structure"></a>VerifyInheritanceHelper 结构

支持 WRL 基础结构，不应在代码中直接使用。

## <a name="syntax"></a>语法

```cpp
template <typename I, typename Base>
struct VerifyInheritanceHelper;

template <typename I>
struct VerifyInheritanceHelper<I, Nil>;
```

### <a name="parameters"></a>参数

*Ⅰ*<br/>
一种类型。

*基地*<br/>
另一种类型。

## <a name="remarks"></a>备注

测试一个接口是否派生自另一个接口。

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

名称                                       | 说明
------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------
[验证继承帮助程序：：验证](#verify) | 测试当前模板参数指定的两个接口，并确定一个接口是否派生自另一个接口。

## <a name="inheritance-hierarchy"></a>继承层次结构

`VerifyInheritanceHelper`

## <a name="requirements"></a>要求

**标题：** 实现.h

**命名空间：** 微软：：WRL：:D

## <a name="verifyinheritancehelperverify"></a><a name="verify"></a>验证继承帮助程序：：验证

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
static void Verify();
```

### <a name="remarks"></a>备注

测试当前模板参数指定的两个接口，并确定一个接口是否派生自另一个接口。

如果一个接口不是从另一个接口派生的，则发出错误。
