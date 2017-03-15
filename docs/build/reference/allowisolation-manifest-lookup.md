---
title: "/ALLOWISOLATION（清单查找） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/ALLOWISOLATION"
  - "VC.Project.VCLinkerTool.AllowIsolation"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/ALLOWISOLATION 链接器选项"
  - "-ALLOWISOLATION 链接器选项"
ms.assetid: 6d41851e-b3c1-4bdf-beaa-031773089d6f
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# /ALLOWISOLATION（清单查找）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指定清单查找行为。  
  
## 语法  
  
```  
/ALLOWISOLATION[:NO]  
```  
  
## 备注  
 **\/ALLOWISOLATION:NO** 指示就像没有清单一样加载 DLL，并且使链接器在可选标头的 `DllCharacteristics` 字段中设置 `IMAGE_DLLCHARACTERISTICS_NO_ISOLATION` 位。  
  
 **\/ALLOWISOLATION** 使操作系统进行清单查找和加载。  
  
 默认为 **\/ALLOWISOLATION** 类型。  
  
 当对可执行程序禁用隔离时，Windows 加载程序不会尝试为新创建的进程查找应用程序清单。  新进程将不具有默认激活上下文，即使在可执行文件内部有清单或者清单放置在与名为 *executable\-name***.exe.manifest** 的可执行文件相同的目录中。  
  
 有关更多信息，请参见[清单文件参考](http://msdn.microsoft.com/library/aa375632)。  
  
### 在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[如何：打开项目属性页](../../misc/how-to-open-project-property-pages.md)。  
  
2.  展开**“配置属性”**节点。  
  
3.  展开**“链接器”**节点。  
  
4.  选择**“清单文件”**属性页。  
  
5.  修改**“允许隔离”**属性。  
  
## 请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)