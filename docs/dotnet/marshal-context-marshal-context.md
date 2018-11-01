---
title: marshal_context::marshal_context
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- msclr::interop::marshal_context::marshal_context
- marshal_context::marshal_context
- msclr.interop.marshal_context.marshal_context
- marshal_context.marshal_context
helpviewer_keywords:
- marshal_context class [C++], operations
ms.assetid: 5f08c895-60b0-4f72-97ff-7ae37c68e853
ms.openlocfilehash: a1a62c47450224aa2bcacde75038adf7a8cfbb9d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50532582"
---
# <a name="marshalcontextmarshalcontext"></a>marshal_context::marshal_context

构造`marshal_context`要用于托管和本机数据类型之间的数据转换对象。

## <a name="syntax"></a>语法

```
marshal_context();
```

## <a name="remarks"></a>备注

某些数据转换需要封送上下文。 请参阅[Overview of Marshaling c + + 中](../dotnet/overview-of-marshaling-in-cpp.md)有关哪些转换需要上下文以及哪些封送文件必须包含在应用程序中的详细信息。

## <a name="example"></a>示例

有关示例，请参阅[marshal_context::marshal_as](../dotnet/marshal-context-marshal-as.md)。

## <a name="requirements"></a>要求

**标头文件：** \<msclr\marshal.h >， \<msclr\marshal_windows.h >， \<msclr\marshal_cppstd.h >，或\<msclr\marshal_atl.h >

**Namespace:** msclr::interop

## <a name="see-also"></a>请参阅

[C++ 中的封送处理概述](../dotnet/overview-of-marshaling-in-cpp.md)<br/>
[marshal_as](../dotnet/marshal-as.md)<br/>
[marshal_context 类](../dotnet/marshal-context-class.md)