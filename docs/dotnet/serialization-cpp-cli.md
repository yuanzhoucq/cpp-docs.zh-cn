---
title: "序列化 (C++/CLI) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".NET Framework [C++], 序列化"
  - "托管代码 [C++], 序列化"
  - "NonSerializedAttribute 类, 托管应用程序"
  - "SerializableAttribute 类, 托管应用程序"
  - "序列化 [C++]"
  - "序列化 [C++], 关于序列化"
ms.assetid: 869010ca-74e1-4989-b409-4643cdb94084
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 序列化 (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

<xref:System.SerializableAttribute> 和 <xref:System.NonSerializedAttribute> 类支持托管类（包括个别字段或属性）的序列化（将对象或成员的状态存储在永久介质中的过程）。  
  
## 备注  
 将 **SerializableAttribute** 自定义特性应用于托管类以序列化整个类，或仅应用于特定的字段或属性以序列化托管类的一部分。  使用 **NonSerializedAttribute** 自定义特性使托管类的字段或属性免于序列化。  
  
## 示例  
  
### 说明  
 在下面的示例中，类 `MyClass`（还有属性 `m_nCount`）被标记为可序列化的。  但 `m_nData` 属性未序列化，如 **NonSerialized** 自定义特性所指示的一样：  
  
### 代码  
  
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
  
### 注释  
 注意，这两个特性都可以用其“简称”（**Serializable** 和 **NonSerialized**）来引用。  这一点在[应用特性](../Topic/Applying%20Attributes.md)中做了进一步解释。  
  
## 请参阅  
 [使用 C\+\+\/CLI 进行 .NET 编程](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)