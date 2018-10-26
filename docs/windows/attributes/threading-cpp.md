---
title: 线程处理 （c + + COM 属性） |Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.threading
dev_langs:
- C++
helpviewer_keywords:
- threading attribute
ms.assetid: 9b558cd6-fbf0-4602-aed5-31c068550ce3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 85ffa775fd18b6979fccf4354ce243f017634d02
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50059670"
---
# <a name="threading-c"></a>threading (C++)

指定 COM 对象的线程处理模型。

## <a name="syntax"></a>语法

```cpp
[ threading(model=enumeration) ]
```

### <a name="parameters"></a>参数

*model*<br/>
（可选）以下线程处理模型之一：

- `apartment` （单元线程处理）

- `neutral` （不带用户界面的.NET framework 组件）

- `single` （简单线程处理）

- `free` （自由线程处理）

- `both` （单元和自由线程处理）

默认值为 `apartment`。

## <a name="remarks"></a>备注

**线程**c + + 属性生成的.idl 文件中未显示，但将在 COM 对象的实现中使用。

在 ATL 项目中，如果[组件类](coclass.md)属性也是存在，由指定的线程模型*模型*传递作为模板参数[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)类由插入`coclass`属性。

**线程**属性还能访问[event_source](event-source.md)。

## <a name="example"></a>示例

请参阅[许可](licensed.md)的示例使用的示例**线程**。

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用对象**|**类**，**结构**|
|**可重复**|否|
|**必需的特性**|**coclass**|
|**无效的特性**|无|

有关特性上下文的详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>请参阅

[COM 特性](com-attributes.md)<br/>
[Typedef、Enum、Union 和 Struct 特性](typedef-enum-union-and-struct-attributes.md)<br/>
[类特性](class-attributes.md)<br/>
[针对旧代码的多线程支持 (Visual C++)](../../parallel/multithreading-support-for-older-code-visual-cpp.md)<br/>
[非特定单元](/windows/desktop/cossdk/neutral-apartments)