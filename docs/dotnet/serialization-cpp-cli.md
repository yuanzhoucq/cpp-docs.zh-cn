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
ms.openlocfilehash: 74810328d654787be46794a31d857eb3fd0731ea
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50478138"
---
# <a name="serialization-ccli"></a>序列化 (C++/CLI)

序列化 （存储对象或成员添加到永久性介质的状态的过程） 的托管类 （包括各个字段或属性） 受<xref:System.SerializableAttribute>和<xref:System.NonSerializedAttribute>类。

## <a name="remarks"></a>备注

将应用**SerializableAttribute**于托管类，以序列化整个类或仅向特定字段或属性进行序列化的托管类的部分应用的自定义属性。 使用**nonserializedattribute 特性**从要序列化到的托管类中免除的字段或属性的自定义属性。

## <a name="example"></a>示例

### <a name="description"></a>描述

在下面的示例中，类`MyClass`(和属性`m_nCount`) 被标记为可序列化。 但是，`m_nData`所示，不序列化属性**NonSerialized**自定义属性：

### <a name="code"></a>代码

```
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

请注意，可以使用其"短名称"引用这两个属性 (**Serializable**并**NonSerialized**)。 对此进行进一步[应用属性](/dotnet/standard/attributes/applying-attributes)。

## <a name="see-also"></a>请参阅

[使用 C++/CLI (Visual C++) 进行 .NET 编程](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)