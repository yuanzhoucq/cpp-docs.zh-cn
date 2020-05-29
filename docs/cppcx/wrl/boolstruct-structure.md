---
title: BoolStruct 结构
ms.date: 09/21/2018
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::BoolStruct
- internal/Microsoft::WRL::Details::BoolStruct::Member
helpviewer_keywords:
- Microsoft::WRL::Details::BoolStruct structure
- Microsoft::WRL::Details::BoolStruct::Member data member
ms.assetid: 666eae78-e81d-4fb7-a9e4-1ba617d6d4cd
ms.openlocfilehash: 4f2a5acf6edb824cff2121c1b6444181b5cfcf98
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371856"
---
# <a name="boolstruct-structure"></a>BoolStruct 结构

支持 WRL 基础结构，不应在代码中直接使用。

## <a name="syntax"></a>语法

```cpp
struct BoolStruct;
```

## <a name="remarks"></a>备注

结构`BoolStruct`定义 是否`ComPtr`管理接口的对象生存期。 `BoolStruct`由[BoolType（）](comptr-class.md#operator-microsoft-wrl-details-booltype)运算符在内部使用。

## <a name="members"></a>成员

### <a name="public-data-members"></a>公共数据成员

名称                          | 说明
----------------------------- | ------------------------------------------------------------------------------------------------------------------
[布尔斯特：成员](#member) | 指定[ComPtr](comptr-class.md)正在或不是管理接口的对象生存期。

## <a name="inheritance-hierarchy"></a>继承层次结构

`BoolStruct`

## <a name="requirements"></a>要求

**标题：** 内部.h

**命名空间：** 微软：：WRL：:D

## <a name="boolstructmember"></a><a name="member"></a>布尔斯特：成员

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
int Member;
```

### <a name="remarks"></a>备注

指定[ComPtr](comptr-class.md)正在或不是管理接口的对象生存期。
