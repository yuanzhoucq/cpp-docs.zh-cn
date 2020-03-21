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
ms.openlocfilehash: 7fb22754248e66d7a20292af41a8e1b8ba050451
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/21/2020
ms.locfileid: "80080035"
---
# <a name="marshal_context-class"></a>marshal_context 类

此类将在本机和托管环境之间转换数据。

## <a name="syntax"></a>语法

```cpp
class marshal_context
```

## <a name="remarks"></a>备注

对于需要上下文的数据转换，请使用 `marshal_context` 类。 有关哪些转换需要上下文以及必须包含哪些封送处理文件的详细信息，请参阅[中C++的封送处理概述](../dotnet/overview-of-marshaling-in-cpp.md)。 使用上下文时的封送处理结果直到销毁 `marshal_context` 对象才有效。 若要保留结果，您必须复制数据。

相同的 `marshal_context` 可用于大量数据转换。 以这种方式重用上下文不会影响以前封送调用的结果。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|---------|-----------|
|[marshal_context::marshal_context](#marshal-context)|构造用于在托管和本机数据类型之间进行数据转换的 `marshal_context` 对象。|
|[marshal_context::~marshal_context](#tilde-marshal-context)|销毁 `marshal_context` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|---------|-----------|
|[marshal_context::marshal_as](#marshal-as)|对特定数据对象执行封送处理，以在托管和本机数据类型之间转换它。|

## <a name="requirements"></a>要求

**头文件：** \<msclr\marshal.h >、\<msclr \ marshal_windows .h >、\<msclr \ marshal_cppstd > 或 \<msclr \ marshal_atl >

**命名空间：** msclr：：互操作

## <a name="marshal_contextmarshal_context"></a><a name="marshal-context"></a>marshal_context：： marshal_context

构造用于在托管和本机数据类型之间进行数据转换的 `marshal_context` 对象。

```cpp
marshal_context();
```

### <a name="remarks"></a>备注

某些数据转换需要封送上下文。 若要详细了解哪些翻译需要使用上下文以及哪些封送处理文件必须包含在应用程序中，请参阅[中C++的封送处理概述](../dotnet/overview-of-marshaling-in-cpp.md)。

### <a name="example"></a>示例

请参阅[marshal_context：： marshal_as](../dotnet/marshal-context-marshal-as.md)的示例。

## <a name="marshal_contextmarshal_context"></a><a name="tilde-marshal-context"></a>marshal_context：： ~ marshal_context

销毁 `marshal_context` 对象。

```cpp
~marshal_context();
```

### <a name="remarks"></a>备注

某些数据转换需要封送上下文。 有关哪些翻译需要上下文以及哪些封送文件必须包含在应用程序中的详细信息，请参阅[中C++的封送的概述](../dotnet/overview-of-marshaling-in-cpp.md)。

删除 `marshal_context` 对象将使由此上下文转换的数据失效。 如果要在销毁 `marshal_context` 对象之后保留数据，则必须手动将数据复制到将保持的变量中。

## <a name="marshal_contextmarshal_as"></a><a name="marshal-as"></a>marshal_context：： marshal_as

对特定数据对象执行封送处理，以在托管和本机数据类型之间转换它。

```cpp
To_Type marshal_as<To_Type>(
   From_Type input
);
```

### <a name="parameters"></a>parameters

input<br/>
中要封送到 `To_Type` 变量的值。

### <a name="return-value"></a>返回值

`To_Type` 类型的变量，它是 `input`的转换值。

### <a name="remarks"></a>备注

此函数将对特定数据对象执行封送处理。 仅将此函数用于中的[封送处理C++概述](../dotnet/overview-of-marshaling-in-cpp.md)表中所指示的转换。

如果尝试封送一对不受支持的数据类型，`marshal_as` 将在编译时生成错误[C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md) 。 有关详细信息，请阅读随此错误提供的消息。 对于超出弃用的函数，可以生成 `C4996` 错误。 生成此错误的两种情况是尝试封送一对不受支持的数据类型，并尝试使用 `marshal_as` 进行需要上下文的转换。

封送处理库包含多个标头文件。 任何转换只需要一个文件，但如果您需要进行其他转换，则可以包含其他文件。 `Marshaling Overview in C++`中的表指示每次转换应包含的封送处理文件。

### <a name="example"></a>示例

此示例将为从 `System::String` 到 `const char *` 变量类型的封送处理创建上下文。 在删除上下文的行后，转换后的数据将无效。

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