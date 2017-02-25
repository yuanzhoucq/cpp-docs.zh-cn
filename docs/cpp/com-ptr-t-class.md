---
title: "_com_ptr_t 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "_com_ptr_t"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_com_ptr_t 类"
ms.assetid: 3753a8a0-03d4-4cfd-8a9a-74872ea53971
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# _com_ptr_t 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 `_com_ptr_t` 对象封装 COM 接口指针，被称为“智能”指针。  此模板类通过对 **IUnknown** 成员函数的函数调用来管理资源分配和解除分配：`QueryInterface`、`AddRef` 和 **Release**。  
  
 智能指针通常由 **\_COM\_SMARTPTR\_TYPEDEF** 宏提供的 typedef 定义引用。  此宏采用接口名称和 IID，并利用接口名称与后缀 `Ptr` 声明 `_com_ptr_t` 的专用化。  例如：  
  
```  
_COM_SMARTPTR_TYPEDEF(IMyInterface, __uuidof(IMyInterface));  
```  
  
 声明 `_com_ptr_t` 专用化 **IMyInterfacePtr**。  
  
 [函数模板](../cpp/relational-function-templates.md)集（而非模板类的成员）支持与比较运算符右侧的智能指针进行比较。  
  
### 构造  
  
|||  
|-|-|  
|[\_com\_ptr\_t](../cpp/com-ptr-t-com-ptr-t.md)|构造 `_com_ptr_t` 对象。|  
  
### 低级别运算  
  
|||  
|-|-|  
|[AddRef](../cpp/com-ptr-t-addref.md)|调用封装的接口指针上的 **IUnknown** 的 `AddRef` 成员函数。|  
|[Attach](../cpp/com-ptr-t-attach.md)|封装此智能指针的类型的原始接口指针。|  
|[CreateInstance](../cpp/com-ptr-t-createinstance.md)|创建一个给定了 **CLSID** 或 **ProgID** 的对象的新实例。|  
|[Detach](../cpp/com-ptr-t-detach.md)|提取并返回封装的接口指针。|  
|[GetActiveObject](../cpp/com-ptr-t-getactiveobject.md)|根据 **CLSID** 或 **ProgID** 附加到一个对象的现有实例。|  
|[GetInterfacePtr](../cpp/com-ptr-t-getinterfaceptr.md)|返回封装的接口指针。|  
|[QueryInterface](../cpp/com-ptr-t-queryinterface.md)|调用封装的接口指针上的 **IUnknown** 的 `QueryInterface` 成员函数。|  
|[Release](../cpp/com-ptr-t-release.md)|调用封装的接口指针上的 **IUnknown** 的 **Release** 成员函数。|  
  
### 运算符  
  
|||  
|-|-|  
|[operator \=](../cpp/com-ptr-t-operator-equal.md)|将新值赋给现有 `_com_ptr_t` 对象。|  
|[operators \=\=, \!\=, \<, \>, \<\=, \>\=](../cpp/com-ptr-t-relational-operators.md)|将智能指针对象与另一个智能指针、原始接口指针或 **NULL** 进行比较。|  
|[Extractors](../cpp/com-ptr-t-extractors.md)|提取封装的 COM 接口指针。|  
  
## 结束 Microsoft 专用  
  
## 要求  
 **标题：**comip.h  
  
 **Lib：**comsuppw.lib 或 comsuppwd.lib（有关详细信息，请参阅 [\/Zc:wchar\_t（wchar\_t 是本机类型）](../build/reference/zc-wchar-t-wchar-t-is-native-type.md)）  
  
## 请参阅  
 [编译器 COM 支持类](../cpp/compiler-com-support-classes.md)