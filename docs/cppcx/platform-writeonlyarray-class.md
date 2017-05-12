---
title: "Platform::WriteOnlyArray 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
s.suite: 
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::WriteOnlyArray"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::WriteOnlyArray 类"
ms.assetid: 92d7dd56-ec58-4b8c-88ba-9c903668b687
caps.latest.revision: 11
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 11
---
# Platform::WriteOnlyArray 类
表示一个一维数组，当调用方为要填充的方法传递数组时，可将此一维数组用作输入参数。  
  
 此 ref 类在 vccorlib.h 中声明为私有；因此，它不是通过元数据发出的，只能通过 C\+\+ 使用它。 此类仅用作输入参数，用于接收调用方分配的数组。 此类无法通过用户代码构造。 它允许 C\+\+ 方法直接写入到该数组中，这种模式称为“FillArray”模式。 有关详细信息，请参阅[Array 和 WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)。  
  
## 语法  
  
```cpp  
private ref class WriteOnlyArray<T, 1>  
```  
  
## 成员  
  
### 公共方法  
 这些方法具有内部可访问性，即，只能在 C\+\+ 应用或组件中访问这些方法。  
  
|名称|描述|  
|--------|--------|  
|[WriteOnlyArray::begin 方法](../cppcx/writeonlyarray-begin-method.md)|指向数组中第一个元素的迭代器。|  
|[WriteOnlyArray::Data 属性](../cppcx/writeonlyarray-data-property.md)|指向数据缓冲区的指针。|  
|[WriteOnlyArray::end 方法](../cppcx/writeonlyarray-end-method.md)|指向数组中最后一个元素的下一位置的迭代器。|  
|[WriteOnlyArray::FastPass 属性](../cppcx/writeonlyarray-fastpass-property.md)|指示数组能否使用 FastPass 机制，此机制是系统透明执行的优化。 请勿在你的代码中使用此机制|  
|[WriteOnlyArray::Length 属性](../cppcx/writeonlyarray-length-property.md)|返回数组中的元素数目。|  
|[WriteOnlyArray::set 函数](../cppcx/writeonlyarray-set-function.md)|将指定元素设置为指定值。|  
  
## 继承层次结构  
 `WriteOnlyArray`  
  
## 要求  
 编译器选项：**\/ZW**  
  
 **元数据：**Platform.winmd  
  
 **命名空间：**Platform  
  
## 请参阅  
 [\(NOTINBUILD\) Platform 命名空间](http://msdn.microsoft.com/zh-cn/f3ce3eab-028c-4204-ba9f-9ab8af17c8c4)   
 [用 C\+\+ 创建 Windows 运行时组件](http://msdn.microsoft.com/library/5b7251e6-4271-4f13-af80-c1cf5b1489bf)