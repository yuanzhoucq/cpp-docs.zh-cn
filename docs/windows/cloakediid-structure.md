---
title: CloakedIid 结构
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::CloakedIid
helpviewer_keywords:
- CloakedIid structure
ms.assetid: 82e0e377-ca3a-46bc-b850-ae2c46c15bb5
ms.openlocfilehash: 7340032e91a9b30b72099477b55b88740b3eb68f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50535295"
---
# <a name="cloakediid-structure"></a>CloakedIid 结构

指示对`RuntimeClass`，`Implements`和`ChainInterfaces`： 指定的接口是无法访问 IID 列表中的模板。

## <a name="syntax"></a>语法

```cpp
template<typename T>
struct CloakedIid : T;
```

#### <a name="parameters"></a>参数

*T*<br/>
接口处于隐藏状态 （已掩蔽）。

## <a name="remarks"></a>备注

下面是如何的示例**CloakedIid**使用： `struct MyRuntimeClass : RuntimeClass<CloakedIid<IMyCloakedInterface>> {}`。

## <a name="inheritance-hierarchy"></a>继承层次结构

`T`

`CloakedIid`

## <a name="requirements"></a>要求

**标头：** implements.h

**命名空间：** Microsoft::WRL

## <a name="see-also"></a>请参阅

[Microsoft::WRL Namespace](../windows/microsoft-wrl-namespace.md)