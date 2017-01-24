---
title: "Using Replaceable Parameters (The Registrar&#39;s Preprocessor) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "AddReplacement"
  - "ClearReplacements"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "%MODULE%"
ms.assetid: 0b376994-84a6-4967-8d97-8c01dfc94efe
caps.latest.revision: 12
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Using Replaceable Parameters (The Registrar&#39;s Preprocessor)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可替换参数允许管理员的客户端指定运行时数据。  为此，管理员维护其输入值与在脚本中的可替换参数的替换映射。  管理员进行这些项在运行时。  
  
##  <a name="_atl_using_.25.module.25"></a> 使用%MODULE%  
 [ATL控件向导](../atl/reference/atl-control-wizard.md) 自动生成使用 `%MODULE%`的脚本。  ATL为您的服务器DLL或EXE的物理位置使用此可替换参数。  
  
## 连接与脚本数据的运行时数据  
 给预处理器的还可以连接与脚本数据的运行时数据。  例如，假设项所需的包含一个完整路径一个字符串中的“`, 1`”的模块追加在末尾。  首先，定义以下展开:  
  
```  
'MySampleKey' = s '%MODULE%, 1'  
```  
  
 然后，在调用操作方法的一个预先该脚本列表中 [调用脚本](../atl/invoking-scripts.md)，请将替换为映射:  
  
 [!code-cpp[NVC_ATL_Utilities#113](../atl/codesnippet/CPP/using-replaceable-parameters-the-registrar-s-preprocessor_1.cpp)]  
  
 在分析该脚本过程中，控制器外接 `'%MODULE%, 1'` 到 `c:\mycode\mydll.dll, 1`。  
  
> [!NOTE]
>  在注册器脚本，4K是最大标记范围。  \(标记是语法中的所有可识别的元素。\)这包括由预处理器或创建的扩展的标记。  
  
> [!NOTE]
>  若要替换替换值在运行时，撤消在脚本调用 [DECLARE\_REGISTRY\_RESOURCE](../Topic/DECLARE_REGISTRY_RESOURCE.md) 或 [DECLARE\_REGISTRY\_RESOURCEID](../Topic/DECLARE_REGISTRY_RESOURCEID.md) 宏。  相反，请在调用 [CAtlModule::UpdateRegistryFromResourceD](../Topic/CAtlModule::UpdateRegistryFromResourceD.md) 或 [CAtlModule::UpdateRegistryFromResourceS](../Topic/CAtlModule::UpdateRegistryFromResourceS.md)的 `UpdateRegistry` 方法替换为，并将您的一些 **\_ATL\_REGMAP\_ENTRY** 结构。  您的数组 **\_ATL\_REGMAP\_ENTRY** 必须具有至少设置的一项**NULL**，**NULL**{}，因此，此项应总是最后一项。  否则，那么，当 **UpdateRegistryFromResource** 调用，访问冲突错误将生成。  
  
> [!NOTE]
>  在生成输出可执行文件，ATL在路径名称周围自动添加引号的项目创建了在运行时会 **%MODULE%** 注册器脚本参数。  如果不希望路径名包括引号，则使用新的 **%MODULE\_RAW%** 参数。  
>   
>  在生成输出DLL，ATL不添加引号传递到路径名的项目时，如果使用 **%MODULE%** 或 **%MODULE\_RAW%**。  
  
## 请参阅  
 [Creating Registrar Scripts](../atl/creating-registrar-scripts.md)