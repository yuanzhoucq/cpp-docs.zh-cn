---
title: IID_PPV_ARGS_Helper 函数
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- client/IID_PPV_ARGS_Helper
helpviewer_keywords:
- IID_PPV_ARGS_Helper function
ms.assetid: afee9b23-8df1-4575-903f-e9ba748418f0
ms.openlocfilehash: 6b1ab2e8e93fda194532fbc8d6f484aaa91249d8
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212964"
---
# <a name="iid_ppv_args_helper-function"></a>IID_PPV_ARGS_Helper 函数

验证指定参数的类型是否从 `IUnknown` 接口派生。

> [!IMPORTANT]
> 此模板专用化支持 WRL 基础结构，不应在代码中直接使用。 改用[IID_PPV_ARGS](/windows/win32/api/combaseapi/nf-combaseapi-iid_ppv_args) 。

## <a name="syntax"></a>语法

```cpp
template<typename T>
void** IID_PPV_ARGS_Helper(
   _Inout_ Microsoft::WRL::Details::ComPtrRef<T> pp
);
```

### <a name="parameters"></a>参数

*T*<br/>
自变量*pp*的类型。

*pp*<br/>
双向间接指针。

## <a name="return-value"></a>返回值

自变量*pp*强制转换为指向的指针的指针 **`void`** 。

## <a name="remarks"></a>备注

如果模板参数*T*不是从派生的，则会生成编译时错误 `IUnknown` 。

## <a name="requirements"></a>要求

**标头：** client.h
