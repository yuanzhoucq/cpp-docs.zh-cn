---
title: 如何：调试发布版本
ms.date: 11/04/2016
helpviewer_keywords:
- debugging [C++], release builds
- release builds, debugging
ms.assetid: d333e4d1-4e6c-4384-84a9-cb549702da25
ms.openlocfilehash: 6d93fac4e980085c322acb55e6f8758e6cea0a00
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62188954"
---
# <a name="how-to-debug-a-release-build"></a>如何：调试发布版本

可以调试应用程序的发布版本。

### <a name="to-debug-a-release-build"></a>调试发布版本

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](working-with-project-properties.md)。

1. 单击“C/C++”  节点。 将“调试信息格式”  设置为[“C7 兼容(/Z7)”](reference/z7-zi-zi-debug-information-format.md)或“程序数据库(/Zi)”  。

1. 展开“链接器”  ，然后单击“常规”  节点。 将“启用增量链接”  设置为[“否(/INCREMENTAL:NO)”](reference/incremental-link-incrementally.md)。

1. 选择“调试”  节点。 将“生成调试信息”  设置为[“是(/DEBUG)”](reference/debug-generate-debug-info.md)。

1. 选择“优化”  节点。 将“引用”  设置为[“/OPT:REF”](reference/opt-optimizations.md)，并将“启用 COMDAT 折叠”  设置为[“/OPT:ICF”](reference/opt-optimizations.md)。

1. 现在可以调试发布版本应用程序。 若要找到问题，请单步执行代码（或使用实时调试），直到找到发生失败的位置，然后确定错误的参数或代码。

   如果应用程序可在调试版本中正常运行，但在发布版本中失败，则某种编译器优化可能会暴露源代码中的缺陷。 若要隔离该问题，请禁用每个源代码文件的所选优化，直到找到引起问题的文件和优化。 （若要加快该过程，可以将文件分为两个组，对一个组禁用优化，当在某个组中发现问题时，继续划分，直到隔离问题文件。）

   可以使用 [/RTC](reference/rtc-run-time-error-checks.md) 尝试在调试版本中暴露此类 bug。

   有关详细信息，请参阅[优化代码](optimizing-your-code.md)。

## <a name="see-also"></a>请参阅

[修复发行版本问题](fixing-release-build-problems.md)
