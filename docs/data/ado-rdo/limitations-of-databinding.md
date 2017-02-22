---
title: "数据绑定的限制 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "数据绑定 [C++], Visual C++ 中的限制"
ms.assetid: 376d7738-5252-4caa-adda-a5486ab2a2a2
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# 数据绑定的限制
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

数据绑定是快速创建数据应用程序的强大方法。  但是，当前的数据绑定控件结构生来就是双层的。  
  
## 可伸缩性  
 ADO 数据绑定控件只能访问 ADO 数据控件的数据。  RDO 数据绑定控件只能访问 RDO RemoteData 控件的数据。  对于 RDO RemoteData 控件，除了使用双层结构外没有其他的解决办法，而这将导致数据库服务器直接接收所有数据检索请求。  为避免直接连接到数据库服务器，应编写允许访问中间层业务和数据对象的提供程序。  ADO 数据控件连接到这些对象，而不是数据库服务器。  这类中间层对象可以在事务服务器（如 COM\+ 1.0 服务）中被缓存和管理。  
  
## 版本和分发  
 当发布控件的新版本后，必须用新版本测试应用程序。  如果用户的计算机上安装了另一个应用程序，并且它具有不同版本的控件，则必须检查此应用程序。  最后，在发布控件的新版本后，必须将新控件分发到应用程序用户。  
  
 **驱动程序和提供程序**  
  
 数据绑定实际上相当于使用的 ODBC 驱动程序或 OLE DB 提供程序。  由于驱动程序和提供程序负责向数据控件公开数据，因此确保驱动程序或提供程序支持所需的功能很重要。  选择驱动程序或提供程序后，必须确保用户已安装了该驱动程序或提供程序。  这包括安装该驱动程序或提供程序所需的任何中间件。  例如，对于 ODBC Oracle 连接，用户不仅要安装 ODBC Oracle 驱动程序，还要安装 Oracle 的 SQL\*Net 中间件。  对于 Oracle 7.3 服务器连接，建议使用 Microsoft Oracle ODBC 驱动程序。  
  
 **可编程性**  
  
 由于 ActiveX 控件被设计为黑盒子组件，因此可编程性仅限于开发人员对控件接口的访问。  在资源编辑器的数据绑定模型中，编程性通过“插入 ActiveX 控件向导”生成的[包装类](../../data/ado-rdo/wrapper-classes.md)来实现。  如果此向导无法检测 coclass，则不生成包装类，并且没有编程访问。  
  
 尽管存在上述限制，数据绑定还是提供了一种使用 Visual C\+\+ 快速建立原型数据应用程序原型的方法。  如果开发速度很重要，则在设计应用程序时应考虑数据绑定。  
  
## 请参阅  
 [在 Visual C\+\+ 中使用 ActiveX 控件进行数据绑定](../../data/ado-rdo/databinding-with-activex-controls-in-visual-cpp.md)