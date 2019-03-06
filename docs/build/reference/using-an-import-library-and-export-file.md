---
title: 使用导入库和导出文件
ms.date: 11/04/2016
helpviewer_keywords:
- circular exports
- import libraries, using
- export files
ms.assetid: 2634256a-8aa5-4495-8c9e-6cde10e4ed76
ms.openlocfilehash: 75a93d97478050718b3f6c32fa83d7320a38954b
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57412973"
---
# <a name="using-an-import-library-and-export-file"></a>使用导入库和导出文件

（可执行文件或 DLL） 在一个程序时导出到另一个程序，它还会导入，或者如果两个以上程序都将导出到和从每个其他导入，链接这些程序的命令必须提供循环导出。

中没有循环导出的情况下，当链接程序使用的其他程序中，导出时必须指定导出的程序的导入库。 导出程序的导入库链接该导出程序时创建。 因此，必须在链接导出程序之前导入程序。 例如，如果从 ONE.dll 导入 TWO.dll，必须先链接 ONE.dll 并获取导入库 ONE.lib。 然后，链接 TWO.dll 时指定 ONE.lib。 当链接器创建 TWO.dll 时，它还会创建其导入库，TWO.lib。 链接从 TWO.dll 导入的程序时，请使用 TWO.lib。

但是，在循环导出的情况，不能链接所有相互依赖的程序使用其他程序的导入库。 在前面所述，如果 TWO.dll 还将导出到 ONE.dll、 TWO.dll 的导入库不会存在尚未 ONE.dll 链接时的示例。 循环导出存在时，必须使用 LIB 创建的导入库和导出文件的程序之一。

若要开始，请选择一个在其上运行 LIB 的程序。 LIB 命令中列出的所有对象和程序库，并指定 /def。 如果程序使用.def 文件或 /EXPORT 规范，则还应指定这些。

创建导入库 (.lib) 和该程序的导出文件 (.exp) 后，在链接其他程序时使用的导入库。 链接创建每个导出程序生成导入库。 例如，如果 ONE.dll 对对象和导出运行 LIB，则创建 ONE.lib 和 ONE.exp。链接 TWO.dll; 时，现在可以使用 ONE.lib此步骤还创建导入库 TWO.lib。

最后，链接以开头的程序。 LINK 命令中，在指定的对象和程序 LIB 创建计划，和导入库的.exp 文件的库或用于程序所使用的导出库。 若要继续此示例，ONE.dll 链接命令包含 ONE.exp 和 TWO.lib，以及对象和进入 ONE.dll 的库。 在链接命令中; 不能指定 /EXPORT 规范的.def 文件这些不是需要，因为.exp 文件中包含的导出定义。 链接时使用了.exp 文件，链接不会创建导入库，因为它假定一个创建时已创建了.exp 文件。

## <a name="see-also"></a>请参阅

[使用导入库和导出文件](../../build/reference/working-with-import-libraries-and-export-files.md)
