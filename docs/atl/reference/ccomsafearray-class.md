---
title: "CComSafeArray 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CComSafeArray"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComSafeArray 类"
ms.assetid: ee349aef-33db-4c85-bd08-5d86a3c9d53a
caps.latest.revision: 26
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 29
---
# CComSafeArray 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此类是 **SAFEARRAY** 结构的包装器。  
  
## 语法  
  
```  
template <  
   typename T,  
   VARTYPE _vartype = _ATL_AutomationType< T >::type  
>  
class CComSafeArray  
```  
  
#### 参数  
 `T`  
 要存储在数组中的数据类型。  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CComSafeArray::CComSafeArray](../Topic/CComSafeArray::CComSafeArray.md)|构造函数。|  
|[CComSafeArray::~CComSafeArray](../Topic/CComSafeArray::~CComSafeArray.md)|析构函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CComSafeArray::Add](../Topic/CComSafeArray::Add.md)|将一个或多个元素或 **SAFEARRAY** 结构添加到 `CComSafeArray`。|  
|[CComSafeArray::Attach](../Topic/CComSafeArray::Attach.md)|将 **SAFEARRAY** 结构附加到 `CComSafeArray` 对象。|  
|[CComSafeArray::CopyFrom](../Topic/CComSafeArray::CopyFrom.md)|将 **SAFEARRAY** 结构的内容复制到 `CComSafeArray` 对象中。|  
|[CComSafeArray::CopyTo](../Topic/CComSafeArray::CopyTo.md)|创建 `CComSafeArray` 对象的副本。|  
|[CComSafeArray::Create](../Topic/CComSafeArray::Create.md)|创建一个 `CComSafeArray` 对象。|  
|[CComSafeArray::Destroy](../Topic/CComSafeArray::Destroy.md)|销毁 `CComSafeArray` 对象。|  
|[CComSafeArray::Detach](../Topic/CComSafeArray::Detach.md)|从 `CComSafeArray` 对象拆离 **SAFEARRAY**。|  
|[CComSafeArray::GetAt](../Topic/CComSafeArray::GetAt.md)|从一维数组中检索单个元素。|  
|[CComSafeArray::GetCount](../Topic/CComSafeArray::GetCount.md)|返回数组中的元素数目。|  
|[CComSafeArray::GetDimensions](../Topic/CComSafeArray::GetDimensions.md)|返回数组中的维数。|  
|[CComSafeArray::GetLowerBound](../Topic/CComSafeArray::GetLowerBound.md)|返回数组给定维度的下限。|  
|[CComSafeArray::GetSafeArrayPtr](../Topic/CComSafeArray::GetSafeArrayPtr.md)|返回 `m_psa` 数据成员的地址。|  
|[CComSafeArray::GetType](../Topic/CComSafeArray::GetType.md)|返回数组中存储的数据类型。|  
|[CComSafeArray::GetUpperBound](../Topic/CComSafeArray::GetUpperBound.md)|返回数组任意维度的上限。|  
|[CComSafeArray::IsSizable](../Topic/CComSafeArray::IsSizable.md)|测试是否可重设 `CComSafeArray` 对象的大小。|  
|[CComSafeArray::MultiDimGetAt](../Topic/CComSafeArray::MultiDimGetAt.md)|从多维数组中检索单个元素。|  
|[CComSafeArray::MultiDimSetAt](../Topic/CComSafeArray::MultiDimSetAt.md)|设置多维数组中元素的值。|  
|[CComSafeArray::Resize](../Topic/CComSafeArray::Resize.md)|重设 `CComSafeArray` 对象的大小。|  
|[CComSafeArray::SetAt](../Topic/CComSafeArray::SetAt.md)|设置一维数组中元素的值。|  
  
### 公共运算符  
  
|名称|描述|  
|--------|--------|  
|[CComSafeArray::operator LPSAFEARRAY](../Topic/CComSafeArray::operator%20LPSAFEARRAY.md)|将值转换为 **SAFEARRAY** 指针。|  
|[CComSafeArray::operator](../Topic/CComSafeArray::operator.md)|从数组中检索元素。|  
|[CComSafeArray::operator \=](../Topic/CComSafeArray::operator%20=.md)|赋值运算符。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CComSafeArray::m\_psa](../Topic/CComSafeArray::m_psa.md)|此数据成员保留 **SAFEARRAY** 结构的地址。|  
  
## 备注  
 `CComSafeArray` 为 [SAFEARRAY Data Type](http://msdn.microsoft.com/zh-cn/9ec8025b-4763-4526-ab45-390c5d8b3b1e) 类提供包装器，从而可以轻松地创建并管理几乎所有支持 VARIANT 的类型的一维数组和多维数组。  
  
 `CComSafeArray` 可简化数组在进程之间的传递，此外还可以对照上限和下限检查数组索引值，从而提供额外的安全性。  
  
 `CComSafeArray` 的下限可以从任何用户定义值开始；但是，通过 C\+\+ 访问的数组应该使用下限 0。 Visual Basic 等其他语言可以使用其他边界值（例如，\-10 到 10）。  
  
 使用 [CComSafeArray::Create](../Topic/CComSafeArray::Create.md) 可以创建 `CComSafeArray` 对象，使用 [CComSafeArray::Destroy](../Topic/CComSafeArray::Destroy.md) 可将其删除。  
  
 `CComSafeArray` 可以包含以下 VARIANT 数据类型子集：  
  
|VARTYPE|描述|  
|-------------|--------|  
|VT\_I1|char|  
|VT\_I2|short|  
|VT\_I4|int|  
|VT\_I4|long|  
|VT\_I8|longlong|  
|VT\_UI1|byte|  
|VT\_UI2|ushort|  
|VT\_UI4|uint|  
|VT\_UI4|ulong|  
|VT\_UI8|ulonglong|  
|VT\_R4|float|  
|VT\_R8|double|  
|VT\_DECIMAL|十进制指针|  
|VT\_VARIANT|变体指针|  
|VT\_CY|货币数据类型|  
  
## 要求  
 **标头：**atlsafe.h  
  
## 示例  
 [!code-cpp[NVC_ATL_Utilities#75](../../atl/codesnippet/CPP/ccomsafearray-class_1.cpp)]  
  
## 请参阅  
 [SAFEARRAY Data Type](http://msdn.microsoft.com/zh-cn/9ec8025b-4763-4526-ab45-390c5d8b3b1e)   
 [CComSafeArray::Create](../Topic/CComSafeArray::Create.md)   
 [CComSafeArray::Destroy](../Topic/CComSafeArray::Destroy.md)   
 [Class Overview](../../atl/atl-class-overview.md)