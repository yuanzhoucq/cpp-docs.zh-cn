---
title: 线程处理C++ （COM 特性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.threading
helpviewer_keywords:
- threading attribute
ms.assetid: 9b558cd6-fbf0-4602-aed5-31c068550ce3
ms.openlocfilehash: b249eaf61266ed9964e44f6f0ad1c2f12a1b1067
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214495"
---
# <a name="threading-c"></a>threading (C++)

指定 COM 对象的线程模型。

## <a name="syntax"></a>语法

```cpp
[ threading(model=enumeration) ]
```

### <a name="parameters"></a>parameters

*model*<br/>
可有可无以下线程模型之一：

- `apartment` （单元线程）

- `neutral` （.NET Framework 没有用户界面的组件）

- `single` （简单线程处理）

- `free` （自由线程处理）

- `both` （单元和自由线程处理）

默认值是 `apartment`。

## <a name="remarks"></a>备注

**线程** C++属性不显示在生成的 .idl 文件中，而是在 COM 对象的实现中使用。

在 ATL 项目中，如果也存在[coclass](coclass.md)特性，则由*模型*指定的线程模型将作为模板参数传递给[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)类，并由 `coclass` 属性插入。

**线程**属性还保护对[event_source](event-source.md)的访问。

## <a name="example"></a>示例

有关**线程**使用的示例，请参阅[许可](licensed.md)的示例。

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用对象**|**class**、 **struct**|
|**可重复**|否|
|**必需的特性**|**coclass**|
|**无效的特性**|无|

有关特性上下文的详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另请参阅

[COM 特性](com-attributes.md)<br/>
[Typedef、Enum、Union 和 Struct 特性](typedef-enum-union-and-struct-attributes.md)<br/>
[类特性](class-attributes.md)<br/>
[针对旧代码的多线程支持 (Visual C++)](../../parallel/multithreading-support-for-older-code-visual-cpp.md)<br/>
[非特定单元](/windows/win32/cossdk/neutral-apartments)
