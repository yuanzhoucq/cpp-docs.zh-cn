---
title: COM + 1.0，ATL COM + 1.0 组件向导 |Microsoft Docs
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
ms.openlocfilehash: e167d1a8d6b7faa161edb332f1041659c176b323
ms.sourcegitcommit: 997e6b7d336cddb388bb6e9e56527725fcaa0624
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/08/2018
ms.locfileid: "48861780"
---
# <a name="com-10-atl-com-10-component-wizard"></a>COM+ 1.0，ATL COM+ 1.0 组件向导

ATL COM + 1.0 组件向导的此页用于指定支持接口类型和其他接口。

ATL 项目和 ATL COM 类的详细信息，请参阅[ATL COM 桌面组件](../../atl/atl-com-desktop-components.md)。

- **Interface**

   指示该对象支持的接口的类型。 默认情况下，该对象支持双重接口。

   |选项|描述|
   |------------|-----------------|
   |**双**|指定对象支持双重接口 (其 vtable 具有自定义接口函数和后期绑定`IDispatch`方法)。 允许 COM 客户端和自动化控制器都能访问该对象。|
   |**自定义**|指定的对象支持自定义界面 （其 vtable 具有自定义接口函数）。 尤其是跨进程边界，可以快于双重接口自定义界面。<br /><br /> - **自动化兼容**将自动化的支持添加到自定义的接口。 对于特性化项目，设置**oleautomation**中组件类的属性。|

- **Queueable**

   指示客户端可以调用以异步方式使用消息队列此组件。 将特性化的组件宏自定义 (TLBATTR_QUEUEABLE，0) 添加到.h 文件 （特性化项目） 或.idl 文件 （非特性化项目）。

- **支持**

   指示对错误处理和对象控制的额外支持。

   |选项|描述|
   |------------|-----------------|
   |**ISupportErrorInfo**|创建支持[ISupportErrorInfo](../../atl/reference/isupporterrorinfoimpl-class.md)接口使对象可以将错误信息返回到客户端。|
   |**IObjectControl**|提供的三个您对象的访问[IObjectControl](/windows/desktop/api/comsvcs/nn-comsvcs-iobjectcontrol)方法：[激活](/windows/desktop/api/comsvcs/nf-comsvcs-iobjectcontrol-activate)， [CanBePooled](/windows/desktop/api/comsvcs/nf-comsvcs-iobjectcontrol-canbepooled)，以及[停用](/windows/desktop/api/comsvcs/nf-comsvcs-iobjectcontrol-deactivate)。|
   |**IObjectConstruct**|创建支持[IObjectConstruct](/windows/desktop/api/comsvcs/nn-comsvcs-iobjectconstruct)界面，可从其他方法或对象的参数中传递管理。|

- **事务**

   指示该对象支持事务。 包括文件 mtxattr.h.idl 文件 （非特性化项目） 中。

   |选项|描述|
   |------------|-----------------|
   |**支持**|指定该对象是永远不会事务流的根通过将组件属性宏 custom(TLBATTR_TRANS_SUPPORTED,0) 添加到.h 文件 （特性化项目） 或.idl 文件 （非特性化项目）。|
   |**必需**|指定该对象可能会或可能不是通过将组件属性宏 custom(TLBATTR_TRANS_REQUIRED,0) 添加到.h 文件 （特性化项目） 或.idl 文件 （非特性化项目） 事务流的根。|
   |**不支持**|指定该对象不包括的事务。 将组件属性宏 custom(TLBATTR_TRANS_NOTSUPP,0) 添加到.h 文件 （特性化项目） 或.idl 文件 （非特性化项目）。|
   |**新要求**|指定的对象始终是事务流的根通过将组件属性宏 custom(TLBATTR_TRANS_REQNEW,0) 添加到.h 文件 （特性化项目） 或.idl 文件 （非特性化项目）。|

## <a name="see-also"></a>请参阅

[ATL COM+ 1.0 组件向导](../../atl/reference/atl-com-plus-1-0-component-wizard.md)<br/>
[ATL COM + 1.0 组件](../../atl/reference/adding-an-atl-com-plus-1-0-component.md)

