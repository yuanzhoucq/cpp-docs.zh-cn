---
title: （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.in
dev_langs:
- C++
helpviewer_keywords:
- in attribute
ms.assetid: 7b450cc4-4d2e-4910-a195-7487c6b7c373
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 95721a37865d7a129d9533b2b8aba7e45c912235
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42611776"
---
# <a name="in-c"></a>in (C++)

指示参数是要从调用过程传递给被调用过程。

## <a name="syntax"></a>语法

```cpp
[in]
```

## <a name="remarks"></a>备注

**中**c + + 属性具有相同的功能[中](http://msdn.microsoft.com/library/windows/desktop/aa367051)MIDL 特性。

## <a name="example"></a>示例

请参阅[可绑定](../windows/bindable.md)有关如何使用的示例**中**。

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用对象**|接口参数，接口方法|
|**可重复**|否|
|**必需的特性**|无|
|**无效的特性**|**retval**|

有关特性上下文的详细信息，请参见 [特性上下文](../windows/attribute-contexts.md)。

## <a name="see-also"></a>请参阅

[IDL 特性](../windows/idl-attributes.md)  
[参数特性](../windows/parameter-attributes.md)  
[方法特性](../windows/method-attributes.md)  
[defaultvalue](../windows/defaultvalue.md)  
[id](../windows/id.md)  
[out](../windows/out-cpp.md)  