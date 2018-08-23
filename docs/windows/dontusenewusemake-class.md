---
title: DontUseNewUseMake 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::DontUseNewUseMake
dev_langs:
- C++
helpviewer_keywords:
- DontUseNewUseMake class
ms.assetid: 8b38d07b-fc14-4cea-afb9-4c1a7dde0093
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6ce3e391ac0da93ed7571a95ce328a5260a8dd44
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42593602"
---
# <a name="dontusenewusemake-class"></a>DontUseNewUseMake 类

支持 WRL 基础结构，不应在代码中直接使用。

## <a name="syntax"></a>语法

```cpp
class DontUseNewUseMake;
```

## <a name="remarks"></a>备注

阻止使用运算符**新**中`RuntimeClass`。 因此，必须使用[使函数成为](../windows/make-function.md)相反。

## <a name="members"></a>成员

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[DontUseNewUseMake::operator new 运算符](../windows/dontusenewusemake-operator-new-operator.md)|重载运算符**新**，并防止中正在使用`RuntimeClass`。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`DontUseNewUseMake`

## <a name="requirements"></a>要求

**标头：** implements.h

**Namespace:** Microsoft::WRL::Details

## <a name="see-also"></a>请参阅

[Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)  
[Make 函数](../windows/make-function.md)