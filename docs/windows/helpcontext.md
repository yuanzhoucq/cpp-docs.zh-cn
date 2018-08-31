---
title: helpcontext |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.helpcontext
dev_langs:
- C++
helpviewer_keywords:
- helpcontext attribute
ms.assetid: 6fbb022d-a4b7-4989-a02f-7f18a9b0ad96
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5644f99e15685f8f1784cc40886709b05a9a06bd
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43221279"
---
# <a name="helpcontext"></a>helpcontext

指定允许用户查看有关中此元素的信息的上下文 ID**帮助**文件。

## <a name="syntax"></a>语法

```cpp
[ helpcontext(
   id
) ]
```

### <a name="parameters"></a>参数

*id*  
帮助主题的上下文 ID。 请参阅[HTML 帮助： 程序的上下文相关帮助](../mfc/html-help-context-sensitive-help-for-your-programs.md)的上下文 Id 的详细信息。

## <a name="remarks"></a>备注

**Helpcontext** c + + 属性具有相同的功能[helpcontext](/windows/desktop/Midl/helpcontext) MIDL 特性。

## <a name="example"></a>示例

有关示例，请参阅[defaultvalue](../windows/defaultvalue.md)有关如何使用的示例**helpcontext**。

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用对象**|**接口**， **typedef**，**类**，方法、 属性|
|**可重复**|否|
|**必需的特性**|无|
|**无效的特性**|无|

有关详细信息，请参见 [特性上下文](../windows/attribute-contexts.md)。

## <a name="see-also"></a>请参阅

[IDL 特性](../windows/idl-attributes.md)  
[接口特性](../windows/interface-attributes.md)  
[类特性](../windows/class-attributes.md)  
[方法特性](../windows/method-attributes.md)  
[Typedef、Enum、Union 和 Struct 特性](../windows/typedef-enum-union-and-struct-attributes.md)  
[helpfile](../windows/helpfile.md)  
[helpstring](../windows/helpstring.md)  