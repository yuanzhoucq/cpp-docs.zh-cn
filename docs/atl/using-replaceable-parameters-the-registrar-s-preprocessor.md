---
title: 使用可更换参数（ATL 注册器）
ms.date: 11/04/2016
helpviewer_keywords:
- '%MODULE%'
ms.assetid: 0b376994-84a6-4967-8d97-8c01dfc94efe
ms.openlocfilehash: 2474db2de384baa9113ed39aef4d3d9c9048903d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329234"
---
# <a name="using-replaceable-parameters-the-registrar39s-preprocessor"></a>使用可替换参数（注册器&#39;预处理器）

可替换参数允许注册器的客户端指定运行时数据。 为此，注册器维护一个替换映射，在其中输入与脚本中可替换参数关联的值。 注册器在运行时进行这些条目。

## <a name="using-module"></a><a name="_atl_using_.25.module.25"></a>使用 %MODULE%

[ATL 控制向导](../atl/reference/atl-control-wizard.md)会自动生成使用`%MODULE%`的脚本。 ATL 使用此可替换参数来定位服务器的 DLL 或 EXE 的实际位置。

## <a name="concatenating-run-time-data-with-script-data"></a>将运行时数据与脚本数据串联

预处理器的另一个用途是将运行时数据与脚本数据串联。 例如，假设需要一个条目，其中包含一个包含一个完整路径的模块，末尾附加`, 1`了字符串"""。 首先，定义以下扩展：

```
'MySampleKey' = s '%MODULE%, 1'
```

然后，在调用引用[脚本](../atl/invoking-scripts.md)列出的脚本处理方法之一之前，向地图添加替换：

[!code-cpp[NVC_ATL_Utilities#113](../atl/codesnippet/cpp/using-replaceable-parameters-the-registrar-s-preprocessor_1.cpp)]

在分析脚本期间，注册器将`'%MODULE%, 1'``c:\mycode\mydll.dll, 1`扩展到 。

> [!NOTE]
> 在注册器脚本中，4K 是最大令牌大小。 （令牌是语法中的任何可识别元素。这包括由预处理器创建或扩展的令牌。

> [!NOTE]
> 要在运行时替换替换值，请删除脚本中对[DECLARE_REGISTRY_RESOURCE](../atl/reference/registry-macros.md#declare_registry_resource)或[DECLARE_REGISTRY_RESOURCEID](../atl/reference/registry-macros.md#declare_registry_resourceid)宏的调用。 相反，请用调用`UpdateRegistry` [CAtlModule：：更新注册表从资源D](../atl/reference/catlmodule-class.md#updateregistryfromresourced)或[CAtlModule：：更新注册表从资源S](../atl/reference/catlmodule-class.md#updateregistryfromresources)替换它，并传递_ATL_REGMAP_ENTRY结构的数组。 _ATL_REGMAP_ENTRY数组必须至少有一个设置为 [NULL， NULL] 的条目，并且此条目应始终是最后一个条目。 否则，在调用时`UpdateRegistryFromResource`将生成访问冲突错误。

> [!NOTE]
> 构建输出可执行文件的项目时，ATL 会自动在运行时创建的路径名称周围使用 **%MODULE%** 注册器脚本参数添加引号。 如果不希望路径名称包含引号，请改用新的 **%MODULE_RAW% 参数**。
>
> 生成输出 DLL 的项目时，如果使用 **%MODULE%** 或 **%MODULE_RAW%，ATL**将不会向路径名称添加引号。

## <a name="see-also"></a>另请参阅

[Creating Registrar Scripts](../atl/creating-registrar-scripts.md)
