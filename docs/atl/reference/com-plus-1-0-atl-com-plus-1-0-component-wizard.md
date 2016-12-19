---
title: "COM+ 1.0，ATL COM+ 1.0 组件向导 | Microsoft Docs"
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
  - "vc.codewiz.class.atl.mts.options"
dev_langs: 
  - "C++"
ms.assetid: 2fbe259c-6be1-4d0e-9cfe-721c75c97cb1
caps.latest.revision: 11
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# COM+ 1.0，ATL COM+ 1.0 组件向导
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用“ATL COM\+ 1.0 组件向导”的此页指定支持的接口类型和附加接口。  
  
 有关 ATL 项目和 ATL COM 类的更多信息，请参见 [ATL COM Desktop Components](../../atl/atl-com-desktop-components.md)。  
  
 **接口**  
 指示对象支持的接口类型。  默认情况下，对象支持双重接口。  
  
|选项|描述|  
|--------|--------|  
|**双重**|指定对象支持双重接口（其 vtable 具有自定义接口函数和后期绑定 `IDispatch` 方法）。  允许 COM 客户端和自动化控制器访问对象。|  
|**自定义**|指定对象支持自定义接口（其 vtable 具有自定义接口函数）。  自定义接口可比双重接口更快，尤其在跨进程边界时。<br /><br /> -   **Automation compatible** 添加自动化支持对自定义接口。  对于特性化项目，在 coclass 中设置 **oleautomation** 属性。|  
  
 **可列队的**  
 指示客户端可使用消息队列异步调用此组件。  将组件特性化宏自定义 \(TLBATTR\_QUEUEABLE, 0\) 添加到 .h 文件（特性化项目）中或者添加到 .idl 文件（非特性化项目）中。  
  
 **支持**  
 指示对错误处理和对象控制的附加支持。  
  
|选项|描述|  
|--------|--------|  
|**ISupportErrorInfo**|创建 [ISupportErrorInfo](../../atl/reference/isupporterrorinfoimpl-class.md) 接口支持，以便对象可将错误信息返回到客户端。|  
|**IObjectControl**|为对象提供三种 [IObjectControl](http://msdn.microsoft.com/library/windows/desktop/ms686474) 方法访问：[Activate](http://msdn.microsoft.com/library/windows/desktop/ms681303)、[CanBePooled](http://msdn.microsoft.com/library/windows/desktop/ms684322) 和 [Deactivate](http://msdn.microsoft.com/library/windows/desktop/ms687094)。|  
|**IObjectConstruct**|创建 [IObjectConstruct](http://msdn.microsoft.com/library/windows/desktop/ms680583) 接口支持以管理从其他方法或对象传入参数。|  
  
 **事务**  
 指示对象支持事务。  在 .idl 文件中包括 mtxattr.h 文件（非特性化项目）。  
  
|选项|描述|  
|--------|--------|  
|**是否支持**|通过向 .h 文件（特性化项目）或者 .idl 文件（非特性化项目）添加组件属性宏 custom\(TLBATTR\_TRANS\_SUPPORTED,0\)，指定对象从来不是事务流的根。|  
|**必需**|通过向 .h 文件（特性化项目）或者 .idl 文件（非特性化项目）添加组件属性宏 custom\(TLBATTR\_TRANS\_REQUIRED,0\)，指定对象可能是也可能不是事务流的根。|  
|**不支持**|指定对象排除事务。  将组件属性宏 custom\(TLBATTR\_TRANS\_NOTSUPP,0\) 添加到 .h 文件（特性化项目）中或者添加到 .idl 文件（非特性化项目）中。|  
|**需要新建**|通过向 .h 文件（特性化项目）或者 .idl 文件（非特性化项目）添加组件属性宏 custom\(TLBATTR\_TRANS\_REQNEW,0\)，指定对象始终是事务流的根。|  
  
## 请参阅  
 [ATL COM\+ 1.0 组件向导](../../atl/reference/atl-com-plus-1-0-component-wizard.md)   
 [ATL COM\+ 1.0 Component](../../atl/reference/adding-an-atl-com-plus-1-0-component.md)