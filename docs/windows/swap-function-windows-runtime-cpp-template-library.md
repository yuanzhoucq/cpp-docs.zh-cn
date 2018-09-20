---
title: Swap 函数 （Windows 运行时 c + + 模板库） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::Swap
dev_langs:
- C++
ms.assetid: ed134a08-ceb7-4279-aa02-a183c3a426ea
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 512619381ebf44ebcd451484403ec27e1ca869b8
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46437022"
---
# <a name="swap-function-windows-runtime-c-template-library"></a>Swap 函数（Windows 运行时 C++ 模板库）

支持 WRL 基础结构，不应在代码中直接使用。

## <a name="syntax"></a>语法

```cpp
WRL_NOTHROW inline void Swap(
   _Inout_ T& left,
   _Inout_ T& right
);
```

### <a name="parameters"></a>参数

*left*<br/>
第一个参数。

*right*<br/>
第二个参数。

## <a name="return-value"></a>返回值

## <a name="remarks"></a>备注

交换两个指定参数的值。

## <a name="requirements"></a>要求

**标头：** internal.h

**Namespace:** Microsoft::WRL::Details

## <a name="see-also"></a>请参阅

[Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)