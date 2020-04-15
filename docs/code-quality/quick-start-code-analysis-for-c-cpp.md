---
title: 快速入门：C/C++ 代码分析
description: 对 Visual Studio 中的C++代码进行静态分析，以检测常见的编码问题和缺陷。
ms.date: 04/08/2020
ms.topic: conceptual
helpviewer_keywords:
- C/C++ code analysis
- code analysis, C/C++
ms.openlocfilehash: 43866564915ac84d227ccbf347280efe59e33351
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370571"
---
# <a name="quickstart-code-analysis-for-cc"></a>快速入门：C/C++ 代码分析

可以通过常规地运行C 或 C++ 代码的代码分析以提高应用程序的质量。 代码分析可以帮助您找到常见问题和违反良好编程实践的行为。 而且，它发现了难以通过测试发现的缺陷。 其警告与编译器错误和警告不同：它搜索已知会导致问题的特定代码模式。 也就是说，代码是有效的，但仍可能为您或使用代码的其他用户创建问题。

## <a name="configure-rule-sets-for-a-project"></a>配置项目的规则集

1. 在**解决方案资源管理器**中，打开项目名称的快捷方式菜单，然后选择**属性**。

1. 在"**配置**和**平台**"列表中，可以选择生成配置和目标平台。

1. 要在每次使用所选配置生成项目时运行代码分析，请选择 **"在生成时启用代码分析**"复选框。 您还可以通过打开 **"分析"** 菜单，然后选择 *"项目名称***上运行代码分析"** 或 **"在文件上运行代码分析"来手动运行代码分析**。

1. 选择要使用[的规则集](using-rule-sets-to-specify-the-cpp-rules-to-run.md)或创建[自定义规则集](using-rule-sets-to-specify-the-cpp-rules-to-run.md#to-create-a-rule-set-in-a-text-editor)。 如果使用 LLVM/clang-cl，请参阅[在可视化工作室中使用 Clang-Tidy](../code-quality/clang-tidy.md)来配置 Clang-Tidy 分析选项。

### <a name="standard-cc-rule-sets"></a>标准 C/C++规则集

Visual Studio 包括以下本机代码的标准规则集：

| 规则集 | 说明 |
|--|--|
| **C++核心检查算术规则** | 这些规则强制[从C++核心准则中执行与算术运算](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es-expressions-and-statements)相关的检查。 |
| **C++核心检查边界规则** | 这些规则强制执行[C++核心准则的边界配置文件](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#probounds-bounds-safety-profile)。 |
| **C++核心检查类规则** | 这些规则强制[检查与C++核心准则中的类](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c-classes-and-class-hierarchies)有关。 |
| **C++核心检查并发规则** | 这些规则强制[从C++核心准则中进行与并发](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#cpcon-concurrency)相关的检查。 |
| **C++核心检查规则** | 这些规则[从C++核心准则中强制实施与相关](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con-constants-and-immutability)检查相关的检查。 |
| **C++核心检查声明规则** | 这些规则强制检查与[C++核心准则的声明](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#i-interfaces)相关的检查。 |
| **C++核心检查枚举规则** | 这些规则[强制从C++核心准则进行与枚举相关的检查](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-enum)。 |
| **C++核心检查实验规则** | 这些规则收集一些实验性检查。 最终，我们期望这些检查被移动到其他规则集或完全删除。 |
| **C++核心检查功能规则** | 这些规则强制检查与[C++核心准则的功能相关的检查](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f-functions)。 |
| **C++核心检查 GSL 规则** | 这些规则强制[从C++核心准则中执行与准则支持库](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-gsl)相关的检查。 |
| **C++核心检查生存期规则** | 这些规则强制执行[C++核心准则的终身配置文件](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#prolifetime-lifetime-safety-profile)。 |
| **C++核心检查所有者指针规则** | 这些规则[强制从C++核心准则中执行与所有者&lt;&gt; T](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management)相关的资源管理检查。 |
| **C++核心检查原始指针规则** | 这些规则强制实施与[C++核心准则中的原始指针](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management)相关的资源管理检查。 |
| **C++核心检查规则** | 这些规则强制从[C++核心准则](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c-core-guidelines)的支票的子集。 使用此规则集可以包括除枚举和实验规则集之外的所有C++核心检查规则。 |
| **C++核心检查共享指针规则** | 这些规则强制实施与[具有C++核心准则的共享指针语义的类型](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management)相关的资源管理检查。 |
| **C++核心检查 STL 规则** | 这些规则强制[从C++核心准则中执行与C++标准模板库 （STL）](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-stdlib)相关的检查。 |
| **C++核心检查样式规则** | 这些规则强制检查与使用[C++核心准则的表达式和语句](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es-expressions-and-statements)有关。 |
| **C++核心检查类型规则** | 这些规则强制执行[C++核心准则的类型配置文件](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#prosafety-type-safety-profile)。 |
| **C++核心检查唯一指针规则** | 这些规则强制实施与具有[C++核心准则中唯一指针语义](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management)的类型相关的资源管理检查。 |
| **并发检查规则** | 这些规则在C++中强制实施一组 Win32 并发模式检查。 |
| **并发规则** | 将C++核心准则的并发规则添加到**并发检查规则**。 |
| **微软本机最小规则** | 这些规则侧重于本机代码中最关键的问题，包括潜在的安全漏洞和应用程序崩溃。 我们建议您在为本机项目创建的任何自定义规则集中包括此规则集。 |
| **Microsoft 本机建议规则** | 这些规则侧重于本机代码中最关键和最常见的问题。 这些问题包括潜在的安全漏洞和应用程序崩溃。 我们建议您在为本机项目创建的任何自定义规则集中包括此规则集。 此规则集旨在与 Visual Studio 专业版和更高版本配合使用。 它包括**微软原生最小规则中的所有规则**。 |

Visual Studio 包括以下管理代码的标准规则集：

| 规则集 | 说明 |
|--|--|
| **微软基本正确性规则** | 这些规则侧重于逻辑错误和在使用框架 API 时的常见错误。 包括此规则集，以展开由最低推荐规则报告的警告列表中。 |
| **微软基本设计指南规则** | 这些规则侧重于强制实施最佳实践，以使代码易于理解和使用。 如果项目包含库代码，或者想要强制实施易于维护的代码的最佳做法，请包括此规则集。 |
| **微软扩展正确性规则** | 这些规则扩展了基本正确性规则，以最大化报告的逻辑和框架使用错误。 特别强调特定方案，如 COM 互通和移动应用程序。 如果这些方案之一适用于项目或发现项目中的其他问题，请考虑包括此规则集。 |
| **微软扩展设计指南规则** | 这些规则扩展了基本设计准则规则，以最大化报告的可用性和可维护性问题。 特别强调命名准则。 如果项目包含库代码，或者想要强制实施编写可维护代码的最高标准，请考虑包括此规则集。 |
| **微软全球化规则** | 这些规则侧重于在不同语言、区域设置和区域性中使用时阻止应用程序中的数据正确显示的问题。 如果应用程序是本地化和/或全球化的，请包括此规则集。 |
| **微软托管最小规则** | 这些规则侧重于代码分析最准确的代码中最关键的问题。  这些规则的数量很少，它们只打算在有限的 Visual Studio 版本中运行。  将最低推荐规则.规则集与其他视觉工作室版本一起使用。 |
| **微软托管推荐规则** | 这些规则侧重于代码中最关键的问题。 这些问题包括潜在的安全漏洞、应用程序崩溃以及其他重要的逻辑和设计错误。 我们建议您在为项目创建的任何自定义规则集中包括此规则集。 |
| **微软混合 （C++ /CLR） 最小规则** | 这些规则侧重于支持通用语言运行时C++项目中最关键的问题。 这些问题包括潜在的安全漏洞、应用程序崩溃以及其他重要的逻辑和设计错误。 我们建议您在为支持通用语言运行时C++项目创建的任何自定义规则集中包括此规则集。 |
| **微软混合 （C++ /CLR） 推荐规则** | 这些规则侧重于支持通用语言运行时C++项目中最常见的和最关键的问题。 这些问题包括潜在的安全漏洞、应用程序崩溃以及其他重要的逻辑和设计错误。 此规则集设计用于视觉工作室专业版和更高版本。 |
| **微软安全规则** | 此规则集包含所有 Microsoft 安全规则。 包括此规则集，以最大化报告的潜在安全问题的数量。 |

要包括每个规则：

| 规则集 | 说明 |
|--|--|
| **微软所有规则** | 此规则集包含所有规则。 运行此规则集可能会导致报告大量警告。 使用此规则集可以全面了解代码中的所有问题。 它可以帮助您确定哪些更集中的规则集最适合为项目运行。 |

## <a name="run-code-analysis"></a>运行代码分析

在"项目属性"对话框的代码**分析**页上，可以配置代码分析，以便每次生成项目时都运行。 还可手动运行代码分析。

对解决方案运行代码分析：

- 在 **"生成"** 菜单中，选择**在解决方案上运行代码分析**。

对项目运行代码分析：

1. 在解决方案资源管理器中，选择项目的名称。

1. 在 **"生成"** 菜单中，在*项目名称***上选择"运行代码分析**"。

要在文件上运行代码分析，请进行：

1. 在解决方案资源管理器中，选择文件的名称。

1. 在 **"生成"** 菜单中，选择**在"文件上运行代码分析**"，或按**Ctrl_Shift_Alt_F7**。

   编译项目或解决方案，并运行代码分析。 结果将显示在"错误列表"窗口中。

## <a name="analyze-and-resolve-code-analysis-warnings"></a>分析和解决代码分析警告

"错误列表"窗口列出了找到的代码分析警告。 结果将显示在表中。 如果有关特定警告的详细信息可用，则第一列包含扩展控件。 选择它可展开显示，了解有关此问题的其他信息。 如果可能，代码分析会显示行号，并分析导致该警告的逻辑。

有关警告的详细信息（包括问题可能的解决方案），请选择"代码"列中的警告 ID 以显示其相应的联机帮助文章。

双击警告以将光标移动到导致 Visual Studio 代码编辑器中出现警告的代码行。 或者，按"输入所选警告"。

了解问题后，可在代码中解决该问题。 然后，重新运行代码分析，以确保警告不再显示在错误列表中。

## <a name="create-work-items-for-code-analysis-warnings"></a>为代码分析警告创建工作项

可以使用 Visual Studio 中的工作项跟踪功能来记录 bug。 要使用此功能，必须连接到 Azure DevOps 服务器（以前是团队基础服务器）的实例。

### <a name="to-create-a-work-item-for-one-or-more-cc-code-warnings"></a>为一个或多个 C/C++ 代码警告创建工作项

1. 在错误列表中，展开并选择警告

1. 在警告的快捷菜单上，选择 **"创建工作项**"，然后选择工作项类型。

1. Visual Studio 为选定的警告创建一个工作项，并在 IDE 的文档窗口中显示该工作项。

1. 添加任何其他信息，然后选择 **"保存工作项**"。

## <a name="search-and-filter-code-analysis-results"></a>搜索和筛选代码分析结果

可搜索冗长的警告消息列表，也可在多项目解决方案中筛选警告。

- **要按标题或警告 ID 筛选警告**：请在"搜索错误列表"框中输入关键字。

- **要按严重性筛选警告**：默认情况下，代码分析消息将分配**警告**的严重性。 您可以将一个或多个消息的严重性指定为自定义规则集中**的"错误**"。 在 **"错误列表****"** 的严重性列上，选择下拉箭头，然后选择筛选器图标。 选择 **"警告**"或 **"错误**"，仅显示分配相应严重性的消息。 **选择"全部"** 以显示所有邮件。

## <a name="see-also"></a>另请参阅

- [C/C++ 代码分析](../code-quality/code-analysis-for-c-cpp-overview.md)
