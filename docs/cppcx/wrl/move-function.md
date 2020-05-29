---
title: Move 函数
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::Move
helpviewer_keywords:
- Move function
ms.assetid: c9525426-97e8-4d8c-9877-b689d8a0dc67
ms.openlocfilehash: 65fe85e95453165430c7ef3cfd4c4bb2babd9868
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213702"
---
# <a name="move-function"></a>Move 函数

支持 WRL 基础结构，不应在代码中直接使用。

## <a name="syntax"></a>语法

```cpp
template<class T>
inline typename RemoveReference<T>::Type&& Move(
   _Inout_ T&& arg
);
```

### <a name="parameters"></a>parameters

*T*<br/>
自变量类型。

*arg*<br/>
要移动的参数。

## <a name="return-value"></a>返回值

引用或右值引用*特征后的参数参数（* 如果有）已被删除。

## <a name="remarks"></a>备注

将指定的参数从一个位置移动到另一个位置。

有关详细信息，请参阅[右值引用声明符](../../cpp/rvalue-reference-declarator-amp-amp.md)的**移动语义**部分： & &。

## <a name="requirements"></a>要求

**标头：** internal。h

**命名空间：** Microsoft：： WRL：:D etails

## <a name="see-also"></a>另请参阅

[Microsoft::WRL::Details 命名空间](microsoft-wrl-details-namespace.md)
