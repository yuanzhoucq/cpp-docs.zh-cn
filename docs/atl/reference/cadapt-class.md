---
title: "CAdapt Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CAdapt"
  - "ATL.CAdapt<T>"
  - "ATL::CAdapt"
  - "ATL::CAdapt<T>"
  - "CAdapt"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "& 运算符, address-of 运算符"
  - "adapter objects"
  - "address-of 运算符"
  - "CAdapt class"
ms.assetid: 0bb695a5-72fe-43d1-8f39-7e4da6e34765
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CAdapt Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此模板用于包装一些类，这些类将 address\-of 运算符重新定义为返回对象地址之外的内容。  
  
## 语法  
  
```  
  
      template <  
   class T  
>  
class CAdapt  
```  
  
#### 参数  
 `T`  
 已适配的类型。  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CAdapt::CAdapt](../Topic/CAdapt::CAdapt.md)|构造函数。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[CAdapt::operator const T&](../Topic/CAdapt::operator%20const%20T&.md)|返回对 `m_T` 的 `const` 引用。|  
|[CAdapt::operator T&](../Topic/CAdapt::operator%20T&.md)|返回对 `m_T` 的引用。|  
|[CAdapt::operator \<](../Topic/CAdapt::operator%20%3C.md)|将已适配类型的对象与 `m_T` 作比较。|  
|[CAdapt::operator \=](../Topic/CAdapt::operator%20=.md)|将已适配类型的对象分配给 `m_T`。|  
|[CAdapt::operator \=\=](../Topic/CAdapt::operator%20==.md)|将已适配类型的对象与 `m_T` 作比较。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CAdapt::m\_T](../Topic/CAdapt::m_T.md)|正在适配的数据。|  
  
## 备注  
 `CAdapt` 是用于包装类（将 address\-of 运算符 \(`operator &`\) 重新定义为返回对象地址以外的内容）的简单模板。  这样的类的示例包括 ATL 的 `CComBSTR`、`CComPtr` 和 `CComQIPtr` 类，以及编译器 COM 支持类 `_com_ptr_t`。  这些类都将 address\-of 运算符重新定义为返回类的数据成员（对于 `CComBSTR` 是 `BSTR`；对于其他类是接口指针）之一的地址。  
  
 `CAdapt` 的主要作用是隐藏由类 `T` 定义的 address\-of 运算符，但仍保留已适配的类的特征。  通过包含 `T` 类型的公共成员 [m\_T](../Topic/CAdapt::m_T.md)，以及定义转换运算符、比较运算符和复制构造函数来允许将 `CAdapt` 的专用化当做 `T` 类型的对象处理，`CAdapt` 实现了这个作用。  
  
 适配器类 `CAdapt` 很有用，因为某些容器样式类期望能够使用 address\-of 运算符获取其包含的对象的地址。  重新定义 address\-of 运算符可能使此要求无法得到满足，而且通常会导致编译错误并阻止将非适配类型用于期望它“正常工作”的类。  `CAdapt` 围绕这些问题提供了一种方法。  
  
 通常，当你要将 `CComBSTR`、`CComPtr`、`CComQIPtr` 或 `_com_ptr_t` 对象存储在容器样式类中时，你将使用 `CAdapt`。  在大多数情况下，若要支持 C\+\+ 标准，这对于 C\+\+11 标准库容器必需的，但 C\+\+11 标准库容器会自动处理已重载 `operator&()` 的类型。  标准库通过在内部使用 [std::addressof\(\)](../Topic/addressof.md) 获取对象的真实地址来达到这一目的。  
  
## 要求  
 **标头：**atlcomcli.h  
  
## 请参阅  
 [Class Overview](../../atl/atl-class-overview.md)