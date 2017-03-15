---
title: "/APPCONTAINER（Windows 应用商店应用程序） | Microsoft Docs"
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
ms.assetid: 9a432db5-7640-460b-ab18-6f61fa7daf6f
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# /APPCONTAINER（Windows 应用商店应用程序）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指定链接器是否会生成应用程序容器中必须运行的可执行图像。  
  
## 语法  
  
```  
/APPCONTAINER[:NO]  
```  
  
## 备注  
 默认情况下，\/APPCONTAINER 是关闭的。  
  
 此选项修改可执行文件以指示应用程序是否必须在 appcontainer 进程隔离环境中运行。  为必须在 appcontainer 环境中运行的应用程序指定 \/APPCONTAINER \- 例如，[!INCLUDE[win8_appstore_long](../../build/reference/includes/win8_appstore_long_md.md)] 应用程序。（当从模板创建 [!INCLUDE[win8_appstore_long](../../build/reference/includes/win8_appstore_long_md.md)]应用程序时，此选项将在 Visual Studio 中自动设置。）对于桌面应用程序，指定 \/APPCONTAINER:NO 或只需省略该选项。  
  
 [!INCLUDE[win8](../../build/includes/win8_md.md)] 中引入了 \/APPCONTAINER 选项。  
  
### 在 Visual Studio 中设置此链接器选项  
  
1.  打开此项目的**“属性页”**对话框。  有关详细信息，请参阅[如何：打开项目属性页](../../misc/how-to-open-project-property-pages.md)。  
  
2.  展开**“配置属性”**节点。  
  
3.  展开**“链接器”**节点。  
  
4.  选择**“命令行”**属性页。  
  
5.  在“附加选项”，输入 `/APPCONTAINER` 或 `/APPCONTAINER:NO`。  
  
## 请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)