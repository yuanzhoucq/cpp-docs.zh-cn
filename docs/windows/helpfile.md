---
title: helpfile |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.helpfile
dev_langs:
- C++
helpviewer_keywords:
- helpfile attribute
ms.assetid: d75161c1-1363-4019-ae09-e7e3b8a3971e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 37309f9170a1fe78c7db802ca13cc81112be9cbb
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42607372"
---
# <a name="helpfile"></a>helpfile

设置类型库的帮助文件的名称。

## <a name="syntax"></a>语法

```cpp
[ helpfile(
   "filename"
) ]
```

### <a name="parameters"></a>参数

*filename*  
包含的帮助主题文件的名称。

## <a name="remarks"></a>备注

**Helpfile** c + + 属性具有相同的功能[helpfile](http://msdn.microsoft.com/library/windows/desktop/aa366853) MIDL 特性。

## <a name="example"></a>示例

有关示例，请参阅[模块](../windows/module-cpp.md)有关如何使用的示例**helpfile**。

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用对象**|**接口**， **typedef**，**类**，方法中，**属性**|
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
[helpcontext](../windows/helpcontext.md)  
[helpstring](../windows/helpstring.md)  