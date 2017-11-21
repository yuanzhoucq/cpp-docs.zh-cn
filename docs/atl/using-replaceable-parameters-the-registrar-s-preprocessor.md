---
title: "使用可替换参数 （ATL 注册器） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- AddReplacement
- ClearReplacements
dev_langs: C++
helpviewer_keywords: '%MODULE%'
ms.assetid: 0b376994-84a6-4967-8d97-8c01dfc94efe
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6909db6a68a9e637ed0cf8513f49ba306007ce6f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="using-replaceable-parameters-the-registrar39s-preprocessor"></a>使用可替换参数 (注册机构 &#39; s 预处理器）
可替换参数允许注册机构的客户端指定运行时数据。 若要执行此操作，注册机构维护替换映射到其中进入你的脚本中的可替换参数与关联的值。 注册机构使运行时的这些项。  
  
##  <a name="_atl_using_.25.module.25"></a>使用 %模块 %  
 [ATL 控件向导](../atl/reference/atl-control-wizard.md)自动生成的脚本使用`%MODULE%`。 ATL 此可替换参数用于你的服务器的 DLL 或 EXE 的实际位置。  
  
## <a name="concatenating-run-time-data-with-script-data"></a>串联运行时数据与脚本数据  
 预处理器的另一个用途是要连接与脚本数据的运行时数据。 例如，假设一个条目需要包含该字符串的模块的完整路径"`, 1`"末尾追加。 首先，定义以下扩展：  
  
```  
'MySampleKey' = s '%MODULE%, 1'  
```  
  
 然后，然后才能调用脚本处理中列出的方法之一[调用脚本](../atl/invoking-scripts.md)，添加到图的替换：  
  
 [!code-cpp[NVC_ATL_Utilities#113](../atl/codesnippet/cpp/using-replaceable-parameters-the-registrar-s-preprocessor_1.cpp)]  
  
 分析过程中的脚本，注册机构展开`'%MODULE%, 1'`到`c:\mycode\mydll.dll, 1`。  
  
> [!NOTE]
>  在注册机构脚本中，4 K 是令牌的最大大小。 （令牌是在语法中任何可识别的元素。）这包括创建的或由预处理器展开的令牌。  
  
> [!NOTE]
>  在运行时替换的替换值，在脚本中，到删除的调用[DECLARE_REGISTRY_RESOURCE](../atl/reference/registry-macros.md#declare_registry_resource)或[DECLARE_REGISTRY_RESOURCEID](../atl/reference/registry-macros.md#declare_registry_resourceid)宏。 相反，将其替换为你自己`UpdateRegistry`调用的方法[CAtlModule::UpdateRegistryFromResourceD](../atl/reference/catlmodule-class.md#updateregistryfromresourced)或[CAtlModule::UpdateRegistryFromResourceS](../atl/reference/catlmodule-class.md#updateregistryfromresources)，并传递你的阵列的**_ATL_REGMAP_ENTRY**结构。 你的阵列的**_ATL_REGMAP_ENTRY**必须有至少一个条目设置为 {**NULL**，**NULL**}，并且此项应始终是最后一项。 否则，将出现访问冲突错误时生成**UpdateRegistryFromResource**调用。  
  
> [!NOTE]
>  ATL 在生成输出可执行文件的项目，会自动添加在运行时创建的路径名称前后的引号**%模块 %**注册器脚本参数。 如果你不想要包括引号的路径名称，使用新**%module_raw%**参数相反。  
>   
>  当生成输出 DLL 的项目，ATL 将不添加引号引起来的路径名称到如果**%模块 %**或**%module_raw%**使用。  
  
## <a name="see-also"></a>另请参阅  
 [创建注册器脚本](../atl/creating-registrar-scripts.md)

