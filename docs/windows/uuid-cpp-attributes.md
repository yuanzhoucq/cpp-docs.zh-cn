---
title: uuid （c + + 特性） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.uuid
dev_langs:
- C++
helpviewer_keywords:
- uuid attribute
ms.assetid: 90562a94-5e28-451b-a4b0-cadda7f66efe
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8d18b323b255c8549ae275d3e6b88471f134c8b4
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42606775"
---
# <a name="uuid-c-attributes"></a>uuid（C++ 特性）

指定类或接口的唯一 ID。

## <a name="syntax"></a>语法

```cpp
[ uuid(
   "uuid"
) ]
```

### <a name="parameters"></a>参数

*uuid*  
一个 128 位的唯一标识符。

## <a name="remarks"></a>备注

如果未指定的接口或类定义**uuid** c + + 属性，则 Visual c + + 编译器将提供一个。 当指定**uuid**，必须包括引号。

如果未指定**uuid**，则编译器将在一台计算机上的不同的属性项目中生成的接口或类具有相同的名称相同的 GUID。

您可以使用 Uuidgen.exe 或 Guidgen.exe 生成你自己的唯一 Id。 (若要运行这些工具，请单击**启动**然后单击**运行**菜单上。 然后输入所需的工具的名称。）

也不使用 ATL 的项目中使用时，指定**uuid**属性是与指定[uuid](../cpp/uuid-cpp.md) **__declspec**修饰符。 若要检索**uuid**类，可以使用[__uuidof](../cpp/uuidof-operator.md)

## <a name="example"></a>示例

请参阅[可绑定](../windows/bindable.md)的示例使用的示例**uuid**。

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用对象**|**类**， **struct**，**接口**，**联合**，**枚举**|
|**可重复**|否|
|**必需的特性**|无|
|**无效的特性**|无|

有关特性上下文的详细信息，请参见 [特性上下文](../windows/attribute-contexts.md)。

## <a name="see-also"></a>请参阅

[IDL 特性](../windows/idl-attributes.md)  
[接口特性](../windows/interface-attributes.md)  
[类特性](../windows/class-attributes.md)  
[Typedef、Enum、Union 和 Struct 特性](../windows/typedef-enum-union-and-struct-attributes.md)  
[uuid](http://msdn.microsoft.com/library/windows/desktop/aa367302)  