---
title: "CRegKey Class | Microsoft Docs"
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
  - "CRegKey"
  - "ATL::CRegKey"
  - "ATL.CRegKey"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL, 注册表"
  - "CRegKey class"
  - "注册表, 删除键"
  - "注册表, 删除值"
  - "注册表, 写入"
ms.assetid: 3afce82b-ba2c-4c1a-8404-dc969e1af74b
caps.latest.revision: 25
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CRegKey Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类为操作系统注册表的项的方法。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在Windows运行时执行的应用程序。  
  
## 语法  
  
```  
  
class CRegKey  
  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CRegKey::CRegKey](../Topic/CRegKey::CRegKey.md)|构造函数。|  
|[CRegKey::~CRegKey](../Topic/CRegKey::~CRegKey.md)|该析构函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CRegKey::Attach](../Topic/CRegKey::Attach.md)|调用此方法HKEY附加到 `CRegKey` 对象通过设置 [m\_hKey](../Topic/CRegKey::m_hKey.md) 成员句柄 `hKey`。|  
|[CRegKey::Close](../Topic/CRegKey::Close.md)|调用此方法释放 [m\_hKey](../Topic/CRegKey::m_hKey.md) 成员处理并将其设置为NULL。|  
|[CRegKey::Create](../Topic/CRegKey::Create.md)|如果它不存在\)，作为 `hKeyParent`，child调用此方法创建指定的键。|  
|[CRegKey::DeleteSubKey](../Topic/CRegKey::DeleteSubKey.md)|调用此方法从注册表中移除指定的键。|  
|[CRegKey::DeleteValue](../Topic/CRegKey::DeleteValue.md)|调用此方法从 [m\_hKey](../Topic/CRegKey::m_hKey.md)移除值字段中。|  
|[CRegKey::Detach](../Topic/CRegKey::Detach.md)|调用此方法分离 `CRegKey` 对象的 [m\_hKey](../Topic/CRegKey::m_hKey.md) 成员句柄和设置 `m_hKey` 为NULL。|  
|[CRegKey::EnumKey](../Topic/CRegKey::EnumKey.md)|调用此方法枚举打开注册表项的子级。|  
|[CRegKey::Flush](../Topic/CRegKey::Flush.md)|调用此方法以打开注册表项的属性编写所有到注册表。|  
|[CRegKey::GetKeySecurity](../Topic/CRegKey::GetKeySecurity.md)|调用此方法检索保护打开注册表项的安全说明符的副本。|  
|[CRegKey::NotifyChangeKeyValue](../Topic/CRegKey::NotifyChangeKeyValue.md)|此方法通知更改的调用方可以打开注册表项的属性或目录。|  
|[CRegKey::Open](../Topic/CRegKey::Open.md)|调用此方法以打开指定的键和设置 [m\_hKey](../Topic/CRegKey::m_hKey.md) 到此密钥句柄。|  
|[CRegKey::QueryBinaryValue](../Topic/CRegKey::QueryBinaryValue.md)|调用此方法检索指定值名称的二进制数据。|  
|[CRegKey::QueryDWORDValue](../Topic/CRegKey::QueryDWORDValue.md)|调用此方法检索一个数据为指定值名称。|  
|[CRegKey::QueryGUIDValue](../Topic/CRegKey::QueryGUIDValue.md)|调用此方法检索GUID数据为指定值名称。|  
|[CRegKey::QueryMultiStringValue](../Topic/CRegKey::QueryMultiStringValue.md)|调用此方法检索multistring的数据为指定值名称。|  
|[CRegKey::QueryQWORDValue](../Topic/CRegKey::QueryQWORDValue.md)|调用此方法检索QWORD数据为指定值名称。|  
|[CRegKey::QueryStringValue](../Topic/CRegKey::QueryStringValue.md)|调用此方法检索字符串数据为指定值名称。|  
|[CRegKey::QueryValue](../Topic/CRegKey::QueryValue.md)|调用此方法检索数据。[m\_hKey](../Topic/CRegKey::m_hKey.md)的字段指定值。  此方法的早期版本不再支持和标记为 **ATL\_DEPRECATED**。|  
|[CRegKey::RecurseDeleteKey](../Topic/CRegKey::RecurseDeleteKey.md)|调用此方法从注册表中移除指定的密钥和显式移除所有子级。|  
|[CRegKey::SetBinaryValue](../Topic/CRegKey::SetBinaryValue.md)|调用此方法设置注册表项的二进制值。|  
|[CRegKey::SetDWORDValue](../Topic/CRegKey::SetDWORDValue.md)|调用此方法设置注册表项的DWORD值。|  
|[CRegKey::SetGUIDValue](../Topic/CRegKey::SetGUIDValue.md)|调用此方法设置注册表项的GUID值。|  
|[CRegKey::SetKeySecurity](../Topic/CRegKey::SetKeySecurity.md)|调用此方法设置注册表项的安全性。|  
|[CRegKey::SetKeyValue](../Topic/CRegKey::SetKeyValue.md)|调用此方法将数据存储在指定值指定的键字段。|  
|[CRegKey::SetMultiStringValue](../Topic/CRegKey::SetMultiStringValue.md)|调用此方法设置注册表项的multistring的值。|  
|[CRegKey::SetQWORDValue](../Topic/CRegKey::SetQWORDValue.md)|调用此方法设置注册表项的QWORD值。|  
|[CRegKey::SetStringValue](../Topic/CRegKey::SetStringValue.md)|调用此方法设置注册表项的字符串值。|  
|[CRegKey::SetValue](../Topic/CRegKey::SetValue.md)|调用此方法将数据存储在 [m\_hKey](../Topic/CRegKey::m_hKey.md)的字段指定值。  此方法的早期版本不再支持和标记为 **ATL\_DEPRECATED**。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[CRegKey::operator HKEY](../Topic/CRegKey::operator%20HKEY.md)|转换为HKEY的一 `CRegKey` 对象。|  
|[CRegKey::operator \=](../Topic/CRegKey::operator%20=.md)|赋值运算符。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CRegKey::m\_hKey](../Topic/CRegKey::m_hKey.md)|包含注册表项的处理与 `CRegKey` 对象。|  
|[CRegKey::m\_pTM](../Topic/CRegKey::m_pTM.md)|为 `CAtlTransactionManager` 对象的指针|  
  
## 备注  
 `CRegKey` 用于创建和delete键和值的方法在系统注册表。  注册表包含安装一组特定系统组件的定义，如软件版本号，安装的硬件和COM对象逻辑以实际映射。  
  
 `CRegKey` 提供编程接口将写入系统注册表为特定计算机。  例如，打开一个特殊的注册表项，请调用 `CRegKey::Open`。  若要检索或修改数据值，则调用 `CRegKey::QueryValue` 或 `CRegKey::SetValue`，分别。  若要关闭密钥，请调用 `CRegKey::Close`。  
  
 在关闭键时，其注册表数据写入硬盘写入\(刷新）。  此过程可能需要几秒。  如果应用程序必须显式写入注册表数据传递到硬盘，可以调用 [RegFlushKey](http://msdn.microsoft.com/library/windows/desktop/ms724867) Win32函数。  但是，**RegFlushKey** 使用许多系统资源，并应调用，仅当绝对必要。  
  
> [!IMPORTANT]
>  允许调用方指定注册表位置的所有方法可能能读取不信任的数据。  利用 [RegQueryValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724911) 的方法应考虑到此函数没有显式终止的NULL的处理字符串。  应检查两个条件由调用代码。  
  
## 要求  
 **Header:** atlbase.h  
  
## 请参阅  
 [DCOM示例](../../top/visual-cpp-samples.md)   
 [Class Overview](../../atl/atl-class-overview.md)   
 [Registry Overview](http://msdn.microsoft.com/library/windows/desktop/ms724871)   
 [Registry Functions](http://msdn.microsoft.com/library/windows/desktop/ms724875)   
 [Registry Value Types](http://msdn.microsoft.com/library/windows/desktop/ms724884)