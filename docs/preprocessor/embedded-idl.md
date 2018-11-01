---
title: embedded_idl
ms.date: 10/18/2018
f1_keywords:
- embedded_idl
helpviewer_keywords:
- embedded_idl attribute
ms.assetid: f1c1c2e8-3872-4172-8795-8d1288a20452
ms.openlocfilehash: 202d5b23a5e2e8e673e3c220b9618cfe6cd4f0d9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50525601"
---
# <a name="embeddedidl"></a>embedded_idl

**C + + 专用**

指定将类型库写入保留了特性生成的代码的 .tlh 文件。

## <a name="syntax"></a>语法

```
embedded_idl[("param")]
```

### <a name="parameters"></a>参数

*param*<br/>
可以是以下两个值之一：

- **emitidl**： 从类型库导入的类型信息将出现在为特性化项目生成的 IDL 中。  如果不为 `embedded_idl` 指定参数，则这是默认值，并将有效。

- **no_emitidl**： 从类型库导入的类型信息将不会显示在为特性化项目生成的 IDL 中。

## <a name="example"></a>示例

```cpp
// import_embedded_idl.cpp
// compile with: /LD
#include <windows.h>
[module(name="MyLib2")];
#import "\school\bin\importlib.tlb" embedded_idl("no_emitidl")
```

## <a name="remarks"></a>备注

**结束 c + + 专用**

## <a name="see-also"></a>请参阅

[#import 属性](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import 指令](../preprocessor/hash-import-directive-cpp.md)