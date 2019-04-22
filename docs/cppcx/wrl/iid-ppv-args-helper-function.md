---
title: IID_PPV_ARGS_Helper 函数
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- client/IID_PPV_ARGS_Helper
helpviewer_keywords:
- IID_PPV_ARGS_Helper function
ms.assetid: afee9b23-8df1-4575-903f-e9ba748418f0
ms.openlocfilehash: 5ef4dd6c9db2d19e0c8a4143c5b4ed3f0ac75f6a
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "58783852"
---
# <a name="iidppvargshelper-function"></a>IID_PPV_ARGS_Helper 函数

验证指定的参数的类型派生`IUnknown`接口。

> [!IMPORTANT]
> 此模板专用化支持 WRL 基础结构，不应在代码中直接使用。 使用[IID_PPV_ARGS](/windows/desktop/api/combaseapi/nf-combaseapi-iid_ppv_args)相反。

## <a name="syntax"></a>语法

```cpp
template<typename T>
void** IID_PPV_ARGS_Helper(
   _Inout_ Microsoft::WRL::Details::ComPtrRef<T> pp
);
```

### <a name="parameters"></a>参数

*T*<br/>
自变量的类型*pp*。

*pp*<br/>
一个双向间接指针。

## <a name="return-value"></a>返回值

自变量*pp*强制转换为一个指针-到-a-指向**void**。

## <a name="remarks"></a>备注

如果将生成编译时错误的模板参数*T*也不是派生`IUnknown`。

## <a name="requirements"></a>要求

**标头：** client.h

