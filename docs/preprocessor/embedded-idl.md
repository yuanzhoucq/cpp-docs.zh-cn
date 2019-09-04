---
title: embedded_idl 导入属性
ms.date: 08/29/2019
f1_keywords:
- embedded_idl
helpviewer_keywords:
- embedded_idl attribute
ms.assetid: f1c1c2e8-3872-4172-8795-8d1288a20452
ms.openlocfilehash: 01948b171b20ad0a3bf3e7a41047f1fe3df185b0
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216323"
---
# <a name="embedded_idl-import-attribute"></a>embedded_idl 导入属性

**C++相关**

指定是否将类型库写入`.tlh`包含特性生成的代码的文件。

## <a name="syntax"></a>语法

> **#import***类型库***embedded_idl**[ **(** { **"emitidl"**  |  **"no_emitidl"** } **)** ]

### <a name="parameters"></a>参数

**emitidl**\
从*类型库*导入的类型信息出现在为特性化项目生成的 IDL 中。 此行为是默认行为, 并且如果未指定参数`embedded_idl`, 则该行为生效。

**"no_emitidl"** \
从*类型库*导入的类型信息在为特性化项目生成的 IDL 中不存在。

## <a name="example"></a>示例

```cpp
// import_embedded_idl.cpp
// compile with: /LD
#include <windows.h>
[module(name="MyLib2")];
#import "\school\bin\importlib.tlb" embedded_idl("no_emitidl")
```

**结束C++特定**

## <a name="see-also"></a>请参阅

[#import 特性](../preprocessor/hash-import-attributes-cpp.md)\
[#import 指令](../preprocessor/hash-import-directive-cpp.md)
