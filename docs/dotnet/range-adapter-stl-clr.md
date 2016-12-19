---
title: "range_adapter (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::range_adapter"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "range_adapter 类 [STL/CLR]"
ms.assetid: 3fbe2a65-1216-46a0-a182-422816b80cfb
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# range_adapter (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

包装对迭代器用于实现一些基 \(BCL\) 类库的模板类连接。  使用操作 range\_adapter STL\/CLR 范围，就像它 BCL 集合。  
  
## 语法  
  
```  
template<typename Iter>  
    ref class range_adapter  
        :   public  
        System::Collections::IEnumerable,  
        System::Collections::ICollection,  
        System::Collections::Generic::IEnumerable<Value>,  
        System::Collections::Generic::ICollection<Value>  
    { ..... };  
```  
  
#### 参数  
 Iter  
 类型与包装的迭代器。  
  
## 成员  
  
|成员函数|说明|  
|----------|--------|  
|[range\_adapter::range\_adapter](../dotnet/range-adapter-range-adapter-stl-clr.md)|构造适配器对象。|  
  
|运算符|说明|  
|---------|--------|  
|[range\_adapter::operator\=](../dotnet/range-adapter-operator-assign-stl-clr.md)|替换存储的迭代器对。|  
  
## 接口  
  
|接口|说明|  
|--------|--------|  
|<xref:System.Collections.IEnumerable>|在集合元素的循环访问。|  
|<xref:System.Collections.ICollection>|包含了一组元素。|  
|<xref:System.Collections.Generic.IEnumerable%601>|在集合类型元素的循环访问。|  
|<xref:System.Collections.Generic.ICollection%601>|维护一组输入的元素。|  
  
## 备注  
 range\_adapter 存储一对迭代器，又分隔元素的序列。  对象实现可以通过循环访问的四 BCL 接口，在订单。  使用此模板类操作。STL\/CLR 范围非常相似 BCL 容器。  
  
## 要求  
 **标头:** \<cliext\/adapter\>  
  
 **命名空间:** cliext  
  
## 请参阅  
 [collection\_adapter](../dotnet/collection-adapter-stl-clr.md)   
 [make\_collection](../dotnet/make-collection-stl-clr.md)