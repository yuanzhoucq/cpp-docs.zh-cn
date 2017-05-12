---
title: "Platform::Array 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vccorlib/Platform::Array"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::Array 类"
ms.assetid: 7815ab40-88c5-42b0-83b8-081cef0cda31
caps.latest.revision: 9
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 9
---
# Platform::Array 类
表示可以跨应用程序二进制接口 \(ABI\) 接收和传递的一维可修改数组。  
  
## 语法  
  
```cpp  
  
template <typename T>  
    private ref class Array<TArg,1> :   
         public WriteOnlyArray<TArg, 1>,  
         public IBoxArray<TArg>  
  
```  
  
## 成员  
 Platform::Array 从 [Platform::WriteOnlyArray 类](../cppcx/platform-writeonlyarray-class.md) 继承其所有方法，并实现 `Value` 的 [Platform::IBoxArray 接口](../cppcx/platform-iboxarray-interface.md) 属性。  
  
### 公共构造函数  
  
|名称|描述|  
|--------|--------|  
|[Array 构造函数](../cppcx/array-constructors.md)|初始化类模板参数 *T* 指定的类型的一维可修改数组。|  
  
### 方法  
 请参阅 [Platform::WriteOnlyArray 类](../cppcx/platform-writeonlyarray-class.md)。  
  
### 属性  
  
|||  
|-|-|  
|[Array::Value 属性](../cppcx/array-value-property.md)|检索当前数组的句柄。|  
  
## 备注  
 Array 类是密封类，不能被继承。  
  
 Windows 运行时类型系统不支持交错数组的概念，因此无法将 IVector\<Platform::Array\<T\>\> 作为返回值或方法参数传递。 要跨 ABI 传递交错数组或一系列序列，请使用 `IVector<IVector<T>^>`。  
  
 有关何时以及如何使用 Platform::Array 的更多信息，请参见 [Array 和 WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)。  
  
 Windows 运行时类型系统不支持交错数组的概念，因此无法将 IVector\<Platform::Array\<T\>\> 作为返回值或方法参数传递。 要跨 ABI 传递交错数组或一系列序列，请使用 `IVector<IVector<T>^>`。  
  
 此类在编译器会自动包括的 vccorlib.h 标头中定义。 它在 Intellisense 中可见，但在“对象浏览器”中不可见，因为它不是在 platform.winmd 中定义的公共类型。  
  
## 要求  
 编译器选项：**\/ZW**  
  
## 请参阅  
 [Platform 命名空间](../cppcx/platform-namespace-c-cx.md)   
 [Array 和 WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)