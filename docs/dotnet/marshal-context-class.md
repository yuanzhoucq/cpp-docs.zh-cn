---
title: marshal_context 类
ms.date: 01/16/2019
ms.topic: reference
f1_keywords:
- msclr::interop::marshal_context::marshal_context
- msclr::interop::marshal_context::marshal_as
helpviewer_keywords:
- msclr::marshal_context class [C++]
ms.assetid: 241b0cf6-4ca4-4812-aaee-d671c11dc034
ms.openlocfilehash: 25fc2be80ba0e5d8c7f76cee1f22eed4d1bb4fc7
ms.sourcegitcommit: 9813e146a4eb30929d8352872859e8fcb7ff6d2f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54805976"
---
# <a name="marshalcontext-class"></a>marshal_context 类

此类将在本机和托管环境之间转换数据。

## <a name="syntax"></a>语法

```cpp
class marshal_context
```

## <a name="remarks"></a>备注

对于需要上下文的数据转换，请使用 `marshal_context` 类。 有关哪些转换需要上下文以及哪些封送文件必须是包含详细信息，请参阅[的 c + + 中的封送处理概述](../dotnet/overview-of-marshaling-in-cpp.md)。 使用上下文时的封送处理结果直到销毁 `marshal_context` 对象才有效。 若要保留结果，您必须复制数据。

相同`marshal_context`可用于大量数据转换。 重复使用的上下文中这种方式不会影响之前封送处理调用的结果。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|name|描述| 
|---------|-----------| 
|[marshal_context::marshal_context](#marshal-context)|构造`marshal_context`要用于托管和本机数据类型之间的数据转换对象。| 
|[marshal_context::~marshal_context](#tilde-marshal-context)|销毁 `marshal_context` 对象。| 

### <a name="public-methods"></a>公共方法

|name|描述| 
|---------|-----------| 
|[marshal_context::marshal_as](#marshal-as)|对特定数据对象执行封送处理，以在托管和本机数据类型之间转换它。| 


## <a name="requirements"></a>要求

**标头文件：** \<msclr\marshal.h >， \<msclr\marshal_windows.h >， \<msclr\marshal_cppstd.h >，或\<msclr\marshal_atl.h >

**Namespace:** msclr::interop

## <a name="marshal-context"></a>marshal_context::marshal_context

构造`marshal_context`要用于托管和本机数据类型之间的数据转换对象。

```cpp
marshal_context();
```

### <a name="remarks"></a>备注

某些数据转换需要封送上下文。 以详细了解其中哪些转换需要上下文以及哪些封送处理文件必须包含在应用程序中，请参阅[的 c + + 中的封送处理概述](../dotnet/overview-of-marshaling-in-cpp.md)。

### <a name="example"></a>示例

有关示例，请参阅[marshal_context::marshal_as](../dotnet/marshal-context-marshal-as.md)。


## <a name="tilde-marshal-context"></a>marshal_context::~marshal_context

销毁 `marshal_context` 对象。

```cpp
~marshal_context();
```

### <a name="remarks"></a>备注

某些数据转换需要封送上下文。 请参阅[的 c + + 中的封送处理概述](../dotnet/overview-of-marshaling-in-cpp.md)有关哪些转换需要上下文以及哪些封送文件必须包含在应用程序中的详细信息。

删除 `marshal_context` 对象将使由此上下文转换的数据失效。 如果要在销毁 `marshal_context` 对象之后保留数据，则必须手动将数据复制到将保持的变量中。

## <a name="marshal-as"></a>marshal_context::marshal_as

对特定数据对象执行封送处理，以在托管和本机数据类型之间转换它。

```cpp
To_Type marshal_as<To_Type>(
   From_Type input
);
```

### <a name="parameters"></a>参数

*input*<br/>
[in]你想要封送为的值`To_Type`变量。

### <a name="return-value"></a>返回值

类型的变量`To_Type`这是转换后的值的`input`。

### <a name="remarks"></a>备注

此函数将对特定数据对象执行封送处理。 此函数只能用于指示表中的转换[的 c + + 中的封送处理概述](../dotnet/overview-of-marshaling-in-cpp.md)。

如果你尝试封送的数据类型的不受支持，对`marshal_as`将生成错误[C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)在编译时。 读取消息提供此错误以了解更多信息。 `C4996`可为多个只是已弃用的函数生成错误。 生成此错误的两个条件都尝试封送的数据类型不受支持的一对并尝试使用`marshal_as`需要上下文的转换。

封送处理库包含多个标头文件。 任何转换要求只有一个文件，但如果您需要为其他转换，则可以包含其他文件。 `Marshaling Overview in C++`中的表指示每次转换应包含的封送处理文件。

### <a name="example"></a>示例

此示例将为从 `System::String` 到 `const char *` 变量类型的封送处理创建上下文。 转换后的数据将无法删除上下文的行后有效。

```cpp
// marshal_context_test.cpp
// compile with: /clr
#include <stdlib.h>
#include <string.h>
#include <msclr\marshal.h>

using namespace System;
using namespace msclr::interop;

int main() {
   marshal_context^ context = gcnew marshal_context();
   String^ message = gcnew String("Test String to Marshal");
   const char* result;
   result = context->marshal_as<const char*>( message );
   delete context;
   return 0;
}
```