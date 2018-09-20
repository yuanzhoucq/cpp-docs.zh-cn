---
title: marshal_as |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- marshal_as
- msclr.interop.marshal_as
- msclr::interop::marshal_as
dev_langs:
- C++
helpviewer_keywords:
- marshal_as template [C++]
ms.assetid: 2ed717da-2b11-41e5-981d-47d251771989
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 4a745c4d57ae721bb1891990c5621084a055dda3
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46389058"
---
# <a name="marshalas"></a>marshal_as

此方法将本机和托管环境之间的数据转换。

## <a name="syntax"></a>语法

```
To_Type marshal_as<To_Type>(
   From_Type input
);
```

#### <a name="parameters"></a>参数

*input*<br/>
[in]你想要封送为的值`To_Type`变量。

## <a name="return-value"></a>返回值

类型的变量`To_Type`的转换的值，它是`input`。

## <a name="remarks"></a>备注

此方法是本机和托管类型之间转换数据的简化的方法。 若要确定支持哪些数据类型，请参阅[Overview of Marshaling c + + 中](../dotnet/overview-of-marshaling-in-cpp.md)。 某些数据转换需要上下文。 可以使用转换这些数据类型[marshal_context 类](../dotnet/marshal-context-class.md)。

如果你尝试封送数据类型不受支持的一对`marshal_as`将生成错误[C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)在编译时。 读取消息提供此错误以了解更多信息。 `C4996`可为多个只是已弃用的函数生成错误。 一个例子尝试封送一对不受支持的数据类型。

封送处理库包含多个标头文件。 任何转换要求只有一个文件，但如果您需要为其他转换，则可以包含其他文件。 若要查看哪些文件与相关联的转换，请查看中的表中`Marshaling Overview`。 无论何种转换的你想要执行操作，命名空间要求是始终生效。

## <a name="example"></a>示例

此示例将从封送`const char*`到`System::String`变量类型。

```
// marshal_as_test.cpp
// compile with: /clr
#include <stdlib.h>
#include <string.h>
#include <msclr\marshal.h>

using namespace System;
using namespace msclr::interop;

int main() {
   const char* message = "Test String to Marshal";
   String^ result;
   result = marshal_as<String^>( message );
   return 0;
}
```

## <a name="requirements"></a>要求

**标头文件：** \<msclr\marshal.h >， \<msclr\marshal_windows.h >， \<msclr\marshal_cppstd.h >，或\<msclr\marshal_atl.h >

**Namespace:** msclr::interop

## <a name="see-also"></a>请参阅

[C++ 中的封送处理概述](../dotnet/overview-of-marshaling-in-cpp.md)<br/>
[marshal_context 类](../dotnet/marshal-context-class.md)