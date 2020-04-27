---
title: 使用可替换参数（ATL 注册器）
ms.date: 11/04/2016
helpviewer_keywords:
- '%MODULE%'
ms.assetid: 0b376994-84a6-4967-8d97-8c01dfc94efe
ms.openlocfilehash: debbccea5836fa63282b62ff87573160069fb169
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168678"
---
# <a name="using-replaceable-parameters-the-registrar39s-preprocessor"></a>使用可替换参数（注册器&#39;s 预处理器）

可替换参数允许注册机构的客户端指定运行时数据。 为此，注册机构将维护一个替换地图，其中输入与脚本中的可替换参数相关联的值。 注册器会在运行时生成这些项。

## <a name="using-module"></a><a name="_atl_using_.25.module.25"></a>使用% MODULE%

[ATL 控件向导](../atl/reference/atl-control-wizard.md)会自动生成一个使用`%MODULE%`的脚本。 ATL 将此可替换参数用于服务器 DLL 或 EXE 的实际位置。

## <a name="concatenating-run-time-data-with-script-data"></a>将运行时数据与脚本数据串联

预处理器的另一个用途是使用脚本数据来连接运行时数据。 例如，假设需要一个条目，该条目包含指向后面追加了字符串 "`, 1`" 的模块的完整路径。 首先，定义以下扩展：

```rgs
'MySampleKey' = s '%MODULE%, 1'
```

然后，在调用[脚本](../atl/invoking-scripts.md)中列出的某个脚本处理方法之前，添加对该映射的替换：

[!code-cpp[NVC_ATL_Utilities#113](../atl/codesnippet/cpp/using-replaceable-parameters-the-registrar-s-preprocessor_1.cpp)]

在脚本分析期间，注册机构将扩展`'%MODULE%, 1'`到。 `c:\mycode\mydll.dll, 1`

> [!NOTE]
> 在注册器脚本中，4K 是最大标记大小。 （标记是语法中的任何可识别元素。）这包括由预处理器创建或扩展的令牌。

> [!NOTE]
> 若要在运行时替换替换值，请在脚本中删除对[DECLARE_REGISTRY_RESOURCE](../atl/reference/registry-macros.md#declare_registry_resource)或[DECLARE_REGISTRY_RESOURCEID](../atl/reference/registry-macros.md#declare_registry_resourceid)宏的调用。 而是将其替换为你`UpdateRegistry`自己的方法，该方法调用[CAtlModule：： UpdateRegistryFromResourceD](../atl/reference/catlmodule-class.md#updateregistryfromresourced)或[CAtlModule：： UpdateRegistryFromResourceS](../atl/reference/catlmodule-class.md#updateregistryfromresources)，并传递 _ATL_REGMAP_ENTRY 结构的数组。 _ATL_REGMAP_ENTRY 数组至少必须有一个设置为 {NULL，NULL} 的条目，此条目应始终为最后一个条目。 否则，在调用时`UpdateRegistryFromResource`将生成访问冲突错误。

> [!NOTE]
> 生成输出可执行文件的项目时，ATL 会在运行时使用 **% MODULE%** 注册器脚本参数创建的路径名称两侧添加引号。 如果不希望路径名称包含引号，请改用新的 **% MODULE_RAW%** 参数。
>
> 生成输出 DLL 的项目时，如果使用 **% MODULE%** 或 **% MODULE_RAW%** ，ATL 将不会向路径名称添加引号。

## <a name="see-also"></a>另请参阅

[Creating Registrar Scripts](../atl/creating-registrar-scripts.md)
