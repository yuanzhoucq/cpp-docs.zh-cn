---
title: IID_PPV_ARGS_Helper 函数 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/IID_PPV_ARGS_Helper
dev_langs:
- C++
helpviewer_keywords:
- IID_PPV_ARGS_Helper function
ms.assetid: afee9b23-8df1-4575-903f-e9ba748418f0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 32970c9d30e1804071190ee5a57c42fd4b6334af
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/04/2018
ms.locfileid: "43677246"
---
# <a name="iidppvargshelper-function"></a>IID_PPV_ARGS_Helper 函数

验证指定的参数的类型派生`IUnknown`接口。

> [!IMPORTANT]
> 此模板专用化支持 WRL 基础结构，不应在代码中直接使用。 使用[IID_PPV_ARGS](https://msdn.microsoft.com/library/windows/desktop/ee330727.aspx)相反。

## <a name="syntax"></a>语法

```cpp
template<typename T>
void** IID_PPV_ARGS_Helper(
   _Inout_ Microsoft::WRL::Details::ComPtrRef<T> pp
);
```

### <a name="parameters"></a>参数

*T*  
自变量的类型*pp*。

*pp*  
一个双向间接指针。

## <a name="return-value"></a>返回值

自变量*pp*强制转换为一个指针-到-a-指向**void**。

## <a name="remarks"></a>备注

如果将生成编译时错误的模板参数*T*也不是派生`IUnknown`。

## <a name="requirements"></a>要求

**标头：** client.h

