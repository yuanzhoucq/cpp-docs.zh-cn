---
title: "_variant_t 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Variant"
  - "_variant_t"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_variant_t 类"
  - "_variant_t 类, 成员函数"
  - "_variant_t 类, 运算符"
  - "VARIANT 对象"
  - "VARIANT 对象, COM 封装"
ms.assetid: 6a3cbd4e-0ae8-425e-b4cf-ca0df894c93f
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# _variant_t 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 `_variant_t` 将对象封装了 `VARIANT` 数据类型。  类管理将资源分配及释放并根据实际需要将函数调用至 **VariantInit** 和 **VariantClear**。  
  
### 构造  
  
|||  
|-|-|  
|[\_variant\_t](../cpp/variant-t-variant-t.md)|构造 `_variant_t` 对象。|  
  
### 操作  
  
|||  
|-|-|  
|[附加](../cpp/variant-t-attach.md)|附加 **VARIANT** 对象到 `_variant_t` 对象。|  
|[Clear](../cpp/variant-t-clear.md)|清除封装的 **VARIANT** 对象。|  
|[ChangeType](../cpp/variant-t-changetype.md)|将 `_variant_t` 对象的类型更改为指示的 **VARTYPE**。|  
|[分离](../cpp/variant-t-detach.md)|从此 `_variant_t` 对象中分离封装的 **VARIANT** 对象。|  
|[设置字符串](../cpp/variant-t-setstring.md)|将字串符分配到 `_variant_t` 对象。|  
  
### 运算符  
  
|||  
|-|-|  
|[运算符 \=](../cpp/variant-t-operator-equal.md)|将新值添加到现有 `_variant_t` 对象。|  
|[运算符 \=\=, \!\=](../cpp/variant-t-relational-operators.md)|比较两个 `_variant_t` 对象相等或不相等。|  
|[提取器](../cpp/variant-t-extractors.md)|从封装的 **VARIANT** 对象中提取数据。|  
  
## 结束 Microsoft 专用  
  
## 要求  
 **标题：** comutil.h  
  
 **Lib:** comsuppw.lib 或 comsuppwd.lib（有关更多信息，请参见 [\/Zc:wchar\_t（wchar\_t 是本机类型）](../build/reference/zc-wchar-t-wchar-t-is-native-type.md)）  
  
## 请参阅  
 [编译器 COM 支持类](../cpp/compiler-com-support-classes.md)