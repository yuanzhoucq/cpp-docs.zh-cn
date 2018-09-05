---
title: 使用可替换参数 （ATL 注册器） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
f1_keywords:
- AddReplacement
- ClearReplacements
dev_langs:
- C++
helpviewer_keywords:
- '%MODULE%'
ms.assetid: 0b376994-84a6-4967-8d97-8c01dfc94efe
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 828c3881771aa37181822859cc54894e8771c2cb
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2018
ms.locfileid: "43767589"
---
# <a name="using-replaceable-parameters-the-registrar39s-preprocessor"></a>使用可替换参数 (在注册机构&#39;s 预处理器)

可替换参数允许注册机构的客户端可以指定运行时数据。 若要执行此操作，在注册机构来维护替换映射到其中进入与您的脚本中的可替换参数关联的值。 在注册机构将在运行时这些项。

##  <a name="_atl_using_.25.module.25"></a> 使用 %模块 %

[ATL 控件向导](../atl/reference/atl-control-wizard.md)会自动生成的脚本使用`%MODULE%`。 ATL 服务器的 DLL 或 EXE 的实际位置对使用此可替换参数。

## <a name="concatenating-run-time-data-with-script-data"></a>串联的脚本数据的数据，运行时

预处理器的另一个用途是连接脚本数据的运行时数据。 例如，假设需要一个条目包含字符串的模块的完整路径"`, 1`"附加在后面。 首先，定义以下扩展：

```  
'MySampleKey' = s '%MODULE%, 1'  
```

然后，调用前一个脚本的处理方法中列出[调用脚本](../atl/invoking-scripts.md)，向地图添加替代：

[!code-cpp[NVC_ATL_Utilities#113](../atl/codesnippet/cpp/using-replaceable-parameters-the-registrar-s-preprocessor_1.cpp)]

脚本的分析，期间注册机构会`'%MODULE%, 1'`到`c:\mycode\mydll.dll, 1`。

> [!NOTE]
>  在注册器脚本中，4 K 是令牌的最大大小。 （令牌是在语法中任何可识别的元素。）这包括创建或由预处理器扩展的令牌。

> [!NOTE]
>  若要在运行时替换的替换值，删除到脚本中调用[DECLARE_REGISTRY_RESOURCE](../atl/reference/registry-macros.md#declare_registry_resource)或[DECLARE_REGISTRY_RESOURCEID](../atl/reference/registry-macros.md#declare_registry_resourceid)宏。 相反，它将替换为自己`UpdateRegistry`方法，以调用[CAtlModule::UpdateRegistryFromResourceD](../atl/reference/catlmodule-class.md#updateregistryfromresourced)或[CAtlModule::UpdateRegistryFromResourceS](../atl/reference/catlmodule-class.md#updateregistryfromresources)，并将传递在阵列 _ATL_REGMAP_项结构。 _ATL_REGMAP_ENTRY 你数组必须具有至少一个设置为 {NULL，NULL} 的条目和此条目应始终是最后一个条目。 否则，将出现访问冲突错误时生成`UpdateRegistryFromResource`调用。

> [!NOTE]
>  ATL 生成输出可执行文件项目时，会自动添加在运行时创建的路径名称周围的引号 **%模块 %** 注册器脚本参数。 如果不想要包含引号的路径名称，使用新 **%module_raw%** 参数相反。  
>   
>  当生成输出 DLL 的项目，ATL 将不添加引号到的路径名称如果 **%模块 %** 或 **%module_raw%** 使用。

## <a name="see-also"></a>请参阅

[创建注册器脚本](../atl/creating-registrar-scripts.md)

