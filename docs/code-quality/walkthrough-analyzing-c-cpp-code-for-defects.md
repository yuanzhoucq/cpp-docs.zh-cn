---
title: 演练：分析 C/C++缺陷代码
description: 演示如何在 Visual Studio 中使用 Microsoft C++的代码分析。
ms.date: 04/14/2020
ms.topic: conceptual
helpviewer_keywords:
- C/C++, code analysis
- code analysis, walkthroughs
- code, analyzing C/C++
- code analysis tool, walkthroughs
ms.openlocfilehash: fe9b3775199b2a18cf940b99e87852350f1fbea9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370214"
---
# <a name="walkthrough-analyzing-cc-code-for-defects"></a>演练：分析 C/C++缺陷代码

本演练演示如何分析 C/C++代码的潜在代码缺陷。 它使用 C/C++ 代码的代码分析工具。

在本演练中，您将：

- 对本机代码运行代码分析。
- 分析代码缺陷警告。
- 将警告视为错误。
- 对源代码进行一些规范，以改进代码缺陷分析。

## <a name="prerequisites"></a>先决条件

- [CppDemo 示例](../code-quality/demo-sample.md)的副本。
- 对C/C++的基本理解。

## <a name="run-code-analysis-on-native-code"></a>在本机代码上运行代码分析

### <a name="to-run-code-defect-analysis-on-native-code"></a>在本机代码上运行代码缺陷分析

::: moniker range=">=vs-2019"

1. 在视觉工作室中打开 CppDemo 解决方案。

     CppDemo 解决方案现在填充**解决方案资源管理器**。

1. 在 **"生成"** 菜单上，选择 **"重建解决方案**"。

     解决方案生成时没有任何错误或警告。

1. 在**解决方案资源管理器中**，选择代码缺陷项目。

1. 在 **"项目"** 菜单上，选择 **"属性**"。

     将显示"**代码缺陷属性页**"对话框。

1. 选择**代码分析**属性页。

1. 将**生成属性上的启用代码分析**更改为 **"是**"。 选择“确定”以保存更改****。

1. 重建代码缺陷项目。

     代码分析警告显示在 **"错误列表"** 窗口中。

::: moniker-end

::: moniker range="<=vs-2017"

1. 在视觉工作室中打开 CppDemo 解决方案。

     CppDemo 解决方案现在填充**解决方案资源管理器**。

1. 在 **"生成"** 菜单上，选择 **"重建解决方案**"。

     解决方案生成时没有任何错误或警告。

     > [!NOTE]
     > 在 Visual Studio 2017 中，您可能会在`E1097 unknown attribute "no_init_all"`IntelliSense 引擎中看到虚假警告。 可以放心地忽略此警告。

1. 在**解决方案资源管理器中**，选择代码缺陷项目。

1. 在 **"项目"** 菜单上，选择 **"属性**"。

     将显示"**代码缺陷属性页**"对话框。

1. 选择**代码分析**属性页。

1. 选中"**在生成时启用代码分析**"复选框。 选择“确定”以保存更改****。

1. 重建代码缺陷项目。

     代码分析警告显示在 **"错误列表"** 窗口中。

::: moniker-end

### <a name="to-analyze-code-defect-warnings"></a>分析代码缺陷警告

1. 在 **"查看"** 菜单上，选择 **"错误列表**"。

     此菜单项可能不可见。 这取决于您在可视化工作室中选择的开发人员配置文件。 您可能需要在 **"查看"** 菜单上指向**其他 Windows，** 然后选择 **"错误列表**"。

1. 在 **"错误列表"** 窗口中，双击以下警告：

     C6230：语义上不同类型的隐式强制转换：在布尔上下文中使用 HRESULT。

     代码编辑器显示在函数`bool ProcessDomain()`内引起警告的行。 此警告指示`HRESULT`正在"if"语句中使用，其中预期存在布尔结果。 这通常是一个错误，因为当`S_OK`HRESULT 从函数返回时，它表示成功，但当转换为布尔值时，它将评估为`false`。

1. 使用`SUCCEEDED`宏更正此警告，宏将`true`转换为`HRESULT`返回值指示成功时。 您的代码应类似于以下代码：

   ```cpp
   if (SUCCEEDED(ReadUserAccount()))
   ```

1. 在**错误列表中**，双击以下警告：

     C6282：不正确的运算符：在布尔上下文中分配常量。 请考虑改用"*"。

1. 通过测试相等性来更正此警告。 您的代码应类似于以下代码：

   ```cpp
   if ((len == ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != L'\\'))
   ```

1. 通过初始化和`i``j`0 更正**错误列表中**的剩余 C6001 警告。

1. 重建代码缺陷项目。

     项目生成时没有任何警告或错误。

## <a name="correct-source-code-annotation-warnings"></a>正确的源代码注释警告

### <a name="to-enable-the-source-code-annotation-warnings-in-annotationc"></a>在注释.c 中启用源代码注释警告

::: moniker range=">=vs-2019"

1. 在解决方案资源管理器中，选择注释项目。

1. 在 **"项目"** 菜单上，选择 **"属性**"。

     将显示 **"注释属性页**"对话框。

1. 选择**代码分析**属性页。

1. 将**生成属性上的启用代码分析**更改为 **"是**"。 选择“确定”以保存更改****。

::: moniker-end

::: moniker range="<=vs-2017"

1. 在解决方案资源管理器中，选择注释项目。

1. 在 **"项目"** 菜单上，选择 **"属性**"。

     将显示 **"注释属性页**"对话框。

1. 选择**代码分析**属性页。

1. 选中"**在生成时启用代码分析**"复选框。 选择“确定”以保存更改****。

::: moniker-end

### <a name="to-correct-the-source-code-annotation-warnings-in-annotationc"></a>更正注释中的源代码注释警告

1. 重建注释项目。

1. 在 **"生成"** 菜单上，选择 **"在注释上运行代码分析**"。

1. 在**错误列表中**，双击以下警告：

     C6011：取消引用 NULL 指针"newNode"。

     此警告指示调用方检查返回值失败。 在这种情况下，调用 可能会`AllocateNode`返回 NULL 值。 有关 的函数声明，请参阅 注释.h 标头`AllocateNode`文件。

1. 光标位于发生警告的注释.cpp 文件中的位置。

1. 要更正此警告，请使用"if"语句来测试返回值。 您的代码应类似于以下代码：

   ```cpp
   LinkedList* newNode = AllocateNode();
   if (nullptr != newNode)
   {
       newNode->data = value;
       newNode->next = 0;
       node->next = newNode;
   }
   ```

1. 重建注释项目。

     项目生成时没有任何警告或错误。

## <a name="use-source-code-annotation-to-discover-more-issues"></a>使用源代码注释发现更多问题

### <a name="to-use-source-code-annotation"></a>使用源代码注释

1. 批批形式参数和函数`AddTail`的返回值以指示指针值可能为空：

   ```cpp
   _Ret_maybenull_ LinkedList* AddTail(_Maybenull_ LinkedList* node, int value)
   ```

1. 在“生成”菜单上，选择“对解决方案运行代码分析”。********

1. 在**错误列表中**，双击以下警告：

     C6011：取消引用 NULL 指针"节点"。

     此警告指示传递到函数中的节点可能为空。

1. 要更正此警告，请使用函数开头的"if"语句来测试传入的值。 您的代码应类似于以下代码：

   ```cpp
   if (nullptr == node)
   {
        return nullptr;
   }
   ```

1. 在“生成”菜单上，选择“对解决方案运行代码分析”。********

     项目现在生成时没有任何警告或错误。

## <a name="see-also"></a>另请参阅

[演练：分析代码缺陷的托管代码](/visualstudio/code-quality/walkthrough-analyzing-managed-code-for-code-defects)\
[C/C++ 代码分析](../code-quality/code-analysis-for-c-cpp-overview.md)
