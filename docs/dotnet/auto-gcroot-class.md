---
title: auto_gcroot 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- msclr::auto_gcroot
- msclr.auto_gcroot
- auto_gcroot
dev_langs:
- C++
helpviewer_keywords:
- auto_gcroot
ms.assetid: b5790912-265d-463e-a486-47302e91042a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 48412a932ff3752b0613f7045cd88992332b7917
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46423218"
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