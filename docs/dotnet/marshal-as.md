---
title: marshal_as
ms.date: 07/12/2019
ms.topic: reference
f1_keywords:
- marshal_as
- msclr.interop.marshal_as
- msclr::interop::marshal_as
helpviewer_keywords:
- marshal_as template [C++]
ms.assetid: 2ed717da-2b11-41e5-981d-47d251771989
ms.openlocfilehash: 2b2cacb0acf04aa40b3e299bffd7357e04916b16
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2019
ms.locfileid: "79544843"
---
# <a name="marshal_as"></a>marshal_as

此方法在本机和托管环境之间转换数据。

## <a name="syntax"></a>语法

```
To_Type marshal_as<To_Type>(
   From_Type input
);
```

#### <a name="parameters"></a>parameters

input<br/>
中要封送到 `To_Type` 变量的值。

## <a name="return-value"></a>返回值

`To_Type` 类型的变量，它是 `input`的转换值。

## <a name="remarks"></a>备注

此方法是在本机类型和托管类型之间转换数据的一种简单方法。 若要确定支持的数据类型，请参阅[中C++的封送处理概述](../dotnet/overview-of-marshaling-in-cpp.md)。 某些数据转换需要上下文。 您可以使用[Marshal_context 类](../dotnet/marshal-context-class.md)来转换这些数据类型。

如果尝试封送一对不受支持的数据类型，`marshal_as` 将在编译时生成错误[C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md) 。 有关详细信息，请阅读随此错误提供的消息。 对于超出弃用的函数，可以生成 `C4996` 错误。 这种情况的一个示例就是尝试封送一对不受支持的数据类型。

封送处理库包含多个标头文件。 任何转换只需要一个文件，但如果您需要进行其他转换，则可以包含其他文件。 若要查看哪些转换与哪些文件相关联，请查看 `Marshaling Overview`中的表。 无论你要执行何种转换，命名空间要求始终有效。

如果输入参数为 null，则会引发 `System::ArgumentNullException(_EXCEPTION_NULLPTR)`。

## <a name="example"></a>示例

此示例将 `const char*` 封送到 `System::String` 变量类型。

```cpp
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

**头文件：** \<msclr\marshal.h >、\<msclr \ marshal_windows .h >、\<msclr \ marshal_cppstd > 或 \<msclr \ marshal_atl >

**命名空间：** msclr：：互操作

## <a name="see-also"></a>另请参阅

[C++ 中的封送处理概述](../dotnet/overview-of-marshaling-in-cpp.md)<br/>
[marshal_context 类](../dotnet/marshal-context-class.md)
