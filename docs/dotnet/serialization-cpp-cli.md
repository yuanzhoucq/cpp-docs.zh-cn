---
title: 序列化 (C++/CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- serialization [C++]
- SerializableAttribute class, managed applications
- NonSerializedAttribute class, managed applications
- managed code [C++], serializing
- .NET Framework [C++], serialization
- serialization [C++], about serialization
ms.assetid: 869010ca-74e1-4989-b409-4643cdb94084
ms.openlocfilehash: b2dfdcaf1a1f33e89d106d4529ffc9af2d08376b
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2019
ms.locfileid: "79545161"
---
# <a name="serialization-ccli"></a>序列化 (C++/CLI)

<xref:System.SerializableAttribute> 和 <xref:System.NonSerializedAttribute> 类支持序列化（将对象或成员的状态存储到永久性介质）的序列化（包括单个字段或属性）。

## <a name="remarks"></a>备注

将**SerializableAttribute**自定义特性应用于托管类，以便序列化整个类，或仅应用于特定字段或属性以序列化托管类的各个部分。 使用**system.nonserializedattribute**自定义特性来免除要序列化的托管类的字段或属性。

## <a name="example"></a>示例

### <a name="description"></a>说明

在下面的示例中，类 `MyClass` （和属性 `m_nCount`）标记为可序列化。 但是，不会按照非**系列化**自定义特性的指示序列化 `m_nData` 属性：

### <a name="code"></a>代码

```cpp
// serialization_and_mcpp.cpp
// compile with: /LD /clr
using namespace System;

[ Serializable ]
public ref class MyClass {
public:
   int m_nCount;
private:
   [ NonSerialized ]
   int m_nData;
};
```

### <a name="comments"></a>注释

请注意，这两个属性都可以使用其 "short name" （**Serializable**和非**系列化**）来引用。 这将在[应用属性](/dotnet/standard/attributes/applying-attributes)中进一步说明。

## <a name="see-also"></a>另请参阅

[使用 C++/CLI (Visual C++) 进行 .NET 编程](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)
