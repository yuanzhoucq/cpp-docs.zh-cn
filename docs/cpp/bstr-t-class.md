---
title: "_bstr_t 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "_bstr_t"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_bstr_t 类"
  - "BSTR 对象"
  - "BSTR 对象, COM 封装"
ms.assetid: 58841fef-fe21-4a84-aab9-780262b5201f
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# _bstr_t 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 `_bstr_t` 对象可封装 [BSTR 数据类型](http://msdn.microsoft.com/zh-cn/1b2d7d2c-47af-4389-a6b6-b01b7e915228)。  该类通过在适当时对 **SysAllocString**、**SysFreeString** 和其他 `BSTR` API 进行函数调用来管理资源分配和释放。  `_bstr_t` 类使用引用计数来避免开销过大。  
  
### 构造  
  
|||  
|-|-|  
|[\_bstr\_t](../cpp/bstr-t-bstr-t.md)|构造 `_bstr_t` 对象。|  
  
### 操作  
  
|||  
|-|-|  
|[Assign](../cpp/bstr-t-assign.md)|将 `BSTR` 复制到 `_bstr_t` 包装的 `BSTR` 中。|  
|[Attach](../cpp/bstr-t-attach.md)|将 `BSTR` 包装器链接到 `_bstr_t`。|  
|[copy](../cpp/bstr-t-copy.md)|构造封装的 `BSTR` 的副本。|  
|[Detach](../cpp/bstr-t-detach.md)|返回 `_bstr_t` 包装的 `BSTR` 并从 `_bstr_t` 中分离 `BSTR`。|  
|[GetAddress](../cpp/bstr-t-getaddress.md)|指向 `_bstr_t` 包装的 `BSTR`。|  
|[GetBSTR](../cpp/bstr-t-getbstr.md)|指向 `_bstr_t` 包装的 `BSTR` 的开头。|  
|[length](../cpp/bstr-t-length.md)|返回 `_bstr_t` 中的字符数。|  
  
### 运算符  
  
|||  
|-|-|  
|[operator \=](../cpp/bstr-t-operator-equal.md)|将新值赋给现有 `_bstr_t` 对象。|  
|[运算符 \+\=](../cpp/bstr-t-operator-add-equal-plus.md)|将字符附加到 `_bstr_t` 对象的结尾。|  
|[运算符 \+](../cpp/bstr-t-operator-add-equal-plus.md)|串联两个字符串。|  
|[运算符 \!](../cpp/bstr-t-operator-logical-not.md)|检查封装的 `BSTR` 是否为 **NULL** 字符串。|  
|[运算符 \=\=、\!\=、\<、\>、\<\=、\>\=](../cpp/bstr-t-relational-operators.md)|比较两个 `_bstr_t` 对象。|  
|[运算符 wchar\_t\*&#124;char\*](../cpp/bstr-t-wchar-t-star-bstr-t-char-star.md)|提取指向封装的 Unicode 或多字节 `BSTR` 对象的指针。|  
  
## 结束 Microsoft 专用  
  
## 要求  
 **头文件：** comutil.h  
  
 **Lib：**comsuppw.lib 或 comsuppwd.lib（有关详细信息，请参阅 [\/Zc:wchar\_t（wchar\_t 是本机类型）](../build/reference/zc-wchar-t-wchar-t-is-native-type.md)）  
  
## 请参阅  
 [编译器 COM 支持类](../cpp/compiler-com-support-classes.md)