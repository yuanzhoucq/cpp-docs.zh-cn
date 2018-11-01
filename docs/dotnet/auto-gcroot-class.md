---
title: auto_gcroot 类
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- msclr::auto_gcroot
- msclr.auto_gcroot
- auto_gcroot
helpviewer_keywords:
- auto_gcroot
ms.assetid: b5790912-265d-463e-a486-47302e91042a
ms.openlocfilehash: cb89035d928b251c9cc0427612ce6853a96456a9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50534233"
---
# <a name="autogcroot-class"></a>auto_gcroot 类

自动资源管理 (如[auto_ptr 类](../standard-library/auto-ptr-class.md)) 的可用于本机类型中嵌入虚拟句柄。

## <a name="syntax"></a>语法

```cpp
template<typename _element_type>
class auto_gcroot;
```

#### <a name="parameters"></a>参数

*_element_type*<br/>
要嵌入的托管的类型。

## <a name="requirements"></a>要求

**标头文件** \<msclr\auto_gcroot.h >

**Namespace** msclr

## <a name="see-also"></a>请参阅

[auto_gcroot](../dotnet/auto-gcroot.md)<br/>
[auto_gcroot 成员](../dotnet/auto-gcroot-members.md)<br/>
[如何：使用本机类型声明句柄](../dotnet/how-to-declare-handles-in-native-types.md)<br/>
[auto_handle 类](../dotnet/auto-handle-class.md)