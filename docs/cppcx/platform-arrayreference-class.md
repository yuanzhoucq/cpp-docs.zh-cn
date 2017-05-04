---
title: "Platform::ArrayReference 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::ArrayReference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::ArrayReference 类"
ms.assetid: 9ab3b15e-8a60-4600-8fcb-7d6c86284f4b
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 4
---
# Platform::ArrayReference 类
`ArrayReference` 是在你希望用输入数据填充 C 样式数组时可以在输入参数中替换 [Platform::Array^](../cppcx/platform-array-class.md) 的优化类型。  
  
## 语法  
  
```vb  
  
```  
  
```csharp  
  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|描述|  
|--------|--------|  
|[ArrayReference::ArrayReference 构造函数](../cppcx/arrayreference-arrayreference-constructor.md)|初始化 `ArrayReference` 类的新实例。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[ArrayReference::operator\(\) 运算符](../cppcx/arrayreference-operator-call-operator.md)|将此 `ArrayReference` 转换为 `Platform::Array<T>^*`。|  
|[ArrayReference::operator\= 运算符](../cppcx/arrayreference-operator-assign-operator.md)|将另一 `ArrayReference` 的内容分配给此实例。|  
  
## 异常  
  
## 备注  
 通过使用 `ArrayReference` 填充 C 样式数组，可避免在先复制到 `Platform::Array` 变量，然后复制到 C 样式数组时涉及额外的重复操作。 当你使用 `ArrayReference` 时，只有一个复制操作。 有关代码示例，请参阅 [Array 和 WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)。  
  
## 要求  
 **支持的最低客户端版本：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **支持的最低服务器版本：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空间：**Platform  
  
 **标头：**vccorlib.h  
  
## 小节标题  
  
## 请参阅  
 [Platform 命名空间](../cppcx/platform-namespace-c-cx.md)