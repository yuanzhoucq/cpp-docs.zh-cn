---
title: "accelerator_view 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "amprt/Concurrency::accelerator_view"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "accelerator_view 类"
ms.assetid: 9f298c21-bf62-46e0-88b8-01c5c78ef144
caps.latest.revision: 18
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# accelerator_view 类
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

表示 C\+\+ AMP 数据并行快捷键上的虚拟设备抽象。  
  
## 语法  
  
```  
class accelerator_view;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|描述|  
|--------|--------|  
|[accelerator\_view::accelerator\_view 构造函数](../Topic/accelerator_view::accelerator_view%20Constructor.md)|初始化 `accelerator_view` 类的新实例。|  
|[accelerator\_view::~accelerator\_view 析构函数](../Topic/accelerator_view::~accelerator_view%20Destructor.md)|销毁 `accelerator_view` 对象。|  
  
### 公共方法  
  
|名称|描述|  
|--------|--------|  
|[accelerator\_view::create\_marker 方法](../Topic/accelerator_view::create_marker%20Method.md)|返回将来以跟踪目前为止该 `accelerator_view` 对象已提交的所有命令的完成情况。|  
|[accelerator\_view::flush 方法](../Topic/accelerator_view::flush%20Method.md)|将已排队于 `accelerator_view` 对象的所有挂起命令提交给快捷键用于执行。|  
|[accelerator\_view::get\_accelerator 方法](../Topic/accelerator_view::get_accelerator%20Method.md)|返回 `accelerator_view` 对象的 `accelerator` 对象。|  
|[accelerator\_view::get\_is\_auto\_selection 方法](../Topic/accelerator_view::get_is_auto_selection%20Method.md)|返回指示当 `accelerator_view` 对象传递给 [parallel\_for\_each](../Topic/parallel_for_each%20Function%20\(C++%20AMP\).md) 之后运行时是否会自动选择适当快捷键的布尔值。|  
|[accelerator\_view::get\_is\_debug 方法](../Topic/accelerator_view::get_is_debug%20Method.md)|返回指示 `accelerator_view` 对象是否具有用于扩展性错误报告的 DEBUG 层的布尔值。|  
|[accelerator\_view::get\_queuing\_mode 方法](../Topic/accelerator_view::get_queuing_mode%20Method.md)|返回 `accelerator_view` 对象的排队模式。|  
|[accelerator\_view::get\_version 方法](../Topic/accelerator_view::get_version%20Method.md)|返回 `accelerator_view` 的版本。|  
|[accelerator\_view::wait 方法](../Topic/accelerator_view::wait%20Method.md)|等待所有的提供给 `accelerator_view` 对象的命令完成。|  
  
### 公共运算符  
  
|名称|描述|  
|--------|--------|  
|[accelerator\_view::operator\!\= 运算符](../Topic/accelerator_view::operator!=%20Operator.md)|将此 `accelerator_view` 对象与另一个进行比较，如果相同，则返回 `false`；否则返回 `true`。|  
|[accelerator\_view::operator\= 运算符](../Topic/accelerator_view::operator=%20Operator.md)|将指定的 `accelerator_view` 对象的内容复制到此对象中。|  
|[accelerator\_view::operator\=\= 运算符](../Topic/accelerator_view::operator==%20Operator.md)|将此 `accelerator_view` 对象与另一个进行比较，如果相同，则返回 `true`；否则返回 `false`。|  
  
### 公共数据成员  
  
|名称|描述|  
|--------|--------|  
|[accelerator\_view::accelerator 数据成员](../Topic/accelerator_view::accelerator%20Data%20Member.md)|获取 `accelerator_view` 对象的 `accelerator` 对象。|  
|[accelerator\_view::is\_auto\_selection 数据成员](../Topic/accelerator_view::is_auto_selection%20Data%20Member.md)|获取表明当将 `accelerator_view` 对象传递给 [parallel\_for\_each](../Topic/parallel_for_each%20Function%20\(C++%20AMP\).md) 时，运行时是否将自动选择适当的快捷键的布尔值。|  
|[accelerator\_view::is\_debug 数据成员](../Topic/accelerator_view::is_debug%20Data%20Member.md)|获取表明 `accelerator_view` 对象是否为广泛的错误报告启用了调试层的布尔值。|  
|[accelerator\_view::queuing\_mode 数据成员](../Topic/accelerator_view::queuing_mode%20Data%20Member.md)|获取 `accelerator_view` 对象的排队模式。|  
|[accelerator\_view::version 数据成员](../Topic/accelerator_view::version%20Data%20Member.md)|获取加速器的版本。|  
  
## 继承层次结构  
 `accelerator_view`  
  
## 备注  
 `accelerator_view` 对象表示加速器的一个逻辑的、独立的视图。  单个物理计算设备可以有许多逻辑的、独立的 `accelerator_view` 对象。  每个加速器都有默认的 `accelerator_view` 对象。  可以创建附加 `accelerator_view` 对象。  
  
 物理计算机可以在许多客户端线程之间共享。  客户端线程可以以协作方式使用快捷键的同一 `accelerator_view` 对象，或者每个客户端可以通过独立的 `accelerator_view` 对象与计算设备通信，以和其他客户端线程相隔离。  
  
 `accelerator_view` 对象可以具有两个 [queuing\_mode 枚举](../../../parallel/amp/reference/queuing-mode-enumeration.md) 状态的其中一个。  如果排队模式为 `immediate`，则类似于 `copy` 和 `parallel_for_each` 的命令在返回调用方后将被立即发送到相应的加速器设备中。  如果排队模式为 `deferred`，此类命令将在对应于 `accelerator_view` 对象的命令队列排队。  在调用 `flush()` 之前实际上不会将命令发送到设备。  
  
## 要求  
 **标头：**amprt.h  
  
 **命名空间：** 并发  
  
## 请参阅  
 [Concurrency 命名空间 \(C\+\+ AMP\)](../../../parallel/amp/reference/concurrency-namespace-cpp-amp.md)