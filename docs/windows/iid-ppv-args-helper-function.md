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
ms.openlocfilehash: c3964ce5257a6b2398571c9ed3ba5792b5bd9cca
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46384476"
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

