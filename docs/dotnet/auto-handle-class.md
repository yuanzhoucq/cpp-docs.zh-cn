---
title: auto_handle 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- auto_handle, msclr::auto_handle
- msclr.auto_handle
dev_langs:
- C++
helpviewer_keywords:
- auto_handle class
ms.assetid: a65604d1-ecbb-44fd-ae2f-696ddeeed9d6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 6509eaf8797d20303100c9886590bb2971e6c640
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46419147"
---
# <a name="autohandle-class"></a>auto_handle 类

自动资源管理，这可用于托管类型中嵌入虚拟句柄。

## <a name="syntax"></a>语法

```
template<typename _element_type>
ref class auto_handle;
```

#### <a name="parameters"></a>参数

*_element_type*<br/>
要嵌入的托管的类型。

## <a name="requirements"></a>要求

**标头文件** \<msclr\auto_handle.h >

**Namespace** msclr

## <a name="see-also"></a>请参阅

[auto_handle](../dotnet/auto-handle.md)<br/>
[auto_handle 成员](../dotnet/auto-handle-members.md)<br/>
[auto_gcroot 类](../dotnet/auto-gcroot-class.md)