---
title: 序列化 (C + + /cli CLI) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- serialization [C++]
- SerializableAttribute class, managed applications
- NonSerializedAttribute class, managed applications
- managed code [C++], serializing
- .NET Framework [C++], serialization
- serialization [C++], about serialization
ms.assetid: 869010ca-74e1-4989-b409-4643cdb94084
caps.latest.revision: 13
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 6efd56655cb5b262eab7d7f14c197e11466fb8bf
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="serialization-ccli"></a>序列化 (C++/CLI)
序列化 （的过程中存储的对象或成员在永久介质状态） 的托管类 （包括单个字段或属性） 受<xref:System.SerializableAttribute>和<xref:System.NonSerializedAttribute>类。  
  
## <a name="remarks"></a>备注  
 应用**SerializableAttribute**到托管的类，以便序列化整个类或仅为特定字段或属性进行序列化托管类的部分应用的自定义属性。 使用**NonSerializedAttribute**到免除字段或托管类的属性从要序列化的自定义属性。  
  
## <a name="example"></a>示例  
  
### <a name="description"></a>描述  
 在下面的示例中，类`MyClass`(和属性`m_nCount`) 标记为可序列化。 但是，`m_nData`不序列化属性，如所示**所以**自定义属性：  
  
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
 请注意，可以使用其"短名称"引用这两个属性 (**Serializable**和**所以**)。 这做进一步的解释在[应用特性](/dotnet/standard/attributes/applying-attributes)。  
  
## <a name="see-also"></a>请参阅  
 [使用 C++/CLI (Visual C++) 进行 .NET 编程](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)