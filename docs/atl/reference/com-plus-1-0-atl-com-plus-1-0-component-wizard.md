---
title: COM + 1.0，ATL COM + 1.0 组件向导 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.codewiz.class.atl.mts.options
dev_langs:
- C++
ms.assetid: 2fbe259c-6be1-4d0e-9cfe-721c75c97cb1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9a23f148fbdc611c8a11d8116b2e7dff34fc9d8f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="com-10-atl-com-10-component-wizard"></a>COM+ 1.0，ATL COM+ 1.0 组件向导
ATL COM + 1.0 组件向导的此页用于指定接口类型和其他接口必须支持。  
  
 ATL 项目和 ATL COM 类的详细信息，请参阅[ATL COM 桌面组件](../../atl/atl-com-desktop-components.md)。  
  
 **Interface**  
 指示对象支持的接口的类型。 默认情况下，该对象支持双重接口。  
  
|选项|描述|  
|------------|-----------------|  
|**双**|指定对象支持双重接口 (其 vtable 具有自定义接口函数和后期绑定`IDispatch`方法)。 使 COM 客户端和自动化控制器可以访问的对象。|  
|**自定义**|指定对象支持自定义接口 （其 vtable 具有自定义接口函数）。 自定义接口可以比双重接口，更快，尤其是跨进程边界。<br /><br /> -   **自动化兼容**将自动化的支持添加到自定义的接口。 对于特性化项目，设置**oleautomation**在组件类的属性。|  
  
 **Queueable**  
 指示客户端可以调用使用消息队列以异步方式此组件。 将特性化的组件宏自定义 (TLBATTR_QUEUEABLE，0) 添加到.h 文件 （特性化项目） 或.idl 文件 （非特性化项目）。  
  
 **支持**  
 指示对错误处理和对象控制的额外支持。  
  
|选项|描述|  
|------------|-----------------|  
|**ISupportErrorInfo**|创建支持[ISupportErrorInfo](../../atl/reference/isupporterrorinfoimpl-class.md)接口以便对象可以将错误信息返回到客户端。|  
|**IObjectControl**|提供对三个您对象访问[IObjectControl](http://msdn.microsoft.com/library/windows/desktop/ms686474)方法：[激活](http://msdn.microsoft.com/library/windows/desktop/ms681303)， [CanBePooled](http://msdn.microsoft.com/library/windows/desktop/ms684322)，和[停用](http://msdn.microsoft.com/library/windows/desktop/ms687094)。|  
|**IObjectConstruct**|创建支持[IObjectConstruct](http://msdn.microsoft.com/library/windows/desktop/ms680583)界面来管理从其他方法或对象的参数中的传递。|  
  
 **事务**  
 指示对象支持事务。 在.idl 文件 （非特性化项目） 中包括文件 mtxattr.h。  
  
|选项|描述|  
|------------|-----------------|  
|**支持**|指定对象通过添加组件属性宏 custom(TLBATTR_TRANS_SUPPORTED,0) 到.h 文件 （特性化项目） 或.idl 文件 （非特性化项目） 中的是，永远不会了事务流的根。|  
|**必需**|指定对象可能，也可能不是通过添加组件属性宏 custom(TLBATTR_TRANS_REQUIRED,0) 到.h 文件 （特性化项目） 或.idl 文件 （非特性化项目） 的事务流的根。|  
|**不支持**|指定对象，将事务中排除。 将组件属性宏 custom(TLBATTR_TRANS_NOTSUPP,0) 添加到.h 文件 （特性化项目） 或.idl 文件 （非特性化项目）。|  
|**新要求**|指定对象通过添加组件属性宏 custom(TLBATTR_TRANS_REQNEW,0) 到.h 文件 （特性化项目） 或.idl 文件 （非特性化项目） 中的是，始终了事务流的根。|  
  
## <a name="see-also"></a>请参阅  
 [ATL COM + 1.0 组件向导](../../atl/reference/atl-com-plus-1-0-component-wizard.md)   
 [ATL COM + 1.0 组件](../../atl/reference/adding-an-atl-com-plus-1-0-component.md)

