---
title: 如何：管理符号
ms.date: 11/04/2016
f1_keywords:
- vc.editors.symbol.changing
- vc.editors.symbol.restrictions.name
- vc.editors.symbol.changing.value
- vc.editors.symbol.restrictions.value
- vc.editors.symbol.changing.header
- vc.editors.symbol.changing.unassigned
- vc.editors.symbol.shared.calculated
helpviewer_keywords:
- symbol names
- symbols [C++], names
- restrictions, symbol names
- numeric values
- symbols [C++], numeric values
- numeric values, changing symbols
- symbols [C++], value restrictions
- restrictions, symbol values
- resource files [C++], multiple
- Resource Includes dialog box [C++]
- symbol header files [C++], changing names
- symbols [C++], symbol header files
- Resource.h
- symbols [C++], unassigned
- Change Symbol dialog box [C++]
- unassigned symbols
- symbols [C++], deleting
- symbols [C++], read-only
- symbols [C++], shared
- symbols [C++], calculated
- read-only symbols
- symbol directives
- calculated symbols
- shared symbols
ms.assetid: 26541832-8dba-4177-b642-e08f94502ea7
ms.openlocfilehash: 4bc0376b6b5ff402f0cc9f40093e000763ad6656
ms.sourcegitcommit: bec1480a03e7b4070b469a6c131a69f516bbac70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/13/2019
ms.locfileid: "56226366"
---
# <a name="how-to-manage-symbols"></a>如何：管理符号

创建新资源或资源对象时，开发环境会向它分配默认符号名，例如 IDD_DIALOG1。 可以使用[属性窗口](/visualstudio/ide/reference/properties-window)更改默认符号名或更改任何已与资源关联的符号的名称。

对于关联的符号与单个资源，还可以使用**属性**窗口来更改符号值。 可以使用[资源符号对话框](../windows/resource-symbols-dialog-box.md)若要更改的当前未分配给资源的符号的值。

通常情况下所有符号定义都保存在`Resource.h`。 但是，你可能需要更改此包含文件名，以便可以在同一个目录下使用多个资源文件。

将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。

> [!NOTE]
> 如果你的项目尚未包含.rc 文件，请参阅[创建新的资源脚本文件](../windows/how-to-create-a-resource-script-file.md)。

## <a name="symbol-name-restrictions"></a>符号名限制

对符号名的限制如下所示：

- 所有[符号](../windows/symbols-resource-identifiers.md)必须是唯一的应用程序的作用域内。 这样可防止头文件中出现冲突的符号定义。

- 符号名的有效字符包括 A-Z、a-z、0-9 和下划线 (_)。

- 符号名称不能以数字开头，并且仅限于 247 个字符。

- 符号名不能包含空格。

- 符号名不区分大小写，但保留第一个符号定义的大小写。 定义符号的头文件由资源编译器/编辑器和 C++ 程序用于引用资源文件中定义的资源。 对于只有大小写不同的两个符号名，C++ 程序会看到两个单独的符号，而资源编译器/编辑器将这两个名称视为引用单个符号。

   > [!NOTE]
   > 如果不遵循下面概述的标准符号名方案（ID*_[关键字]），并且符号名恰好与资源脚本编译器已知的关键字相同，则尝试生成资源脚本文件会导致看似难以进行诊断的随机错误生成。 若要防止出现此情况，请遵循标准命名方案。

符号名具有描述性前缀，可指示它们所表示的资源或对象的类型。 这些描述性前缀以文本组合 ID 开头。 Microsoft 基础类库 (MFC) 使用下表中所示的符号命名约定。

|类别|前缀|使用|
|--------------|------------|---------|
|资源|IDR_ IDD_ IDC_ IDI_ IDB_|加速器或菜单（以及关联或自定义资源） 对话框 光标 图标 位图|
|菜单项|ID_|Menu item|
|命令|ID_|命令|
|控件和子窗口|IDC_|控件|
|字符串|IDS_|字符串表中的字符串|
|MFC|AFX_|为预定义 MFC 符号保留|

### <a name="to-change-a-symbol-name-id"></a>若要更改符号名 (ID)

1. 在中[资源视图](../windows/resource-view-window.md)，选择的资源。

1. 在中**属性**窗口中，输入新符号名或从现有符号列表中选择**ID**框。

   如果输入新符号名，已自动对其赋值。

可以使用[资源符号对话框](../windows/resource-symbols-dialog-box.md)更改当前未分配给资源的符号的名称。

## <a name="symbol-value-restrictions"></a>符号值限制

符号值可以是用于 #define 预处理器指令的以正常方式表示的任何整数。 下面是符号值的一些示例：

```
18
4001
0x0012
-3456
```

资源（加速器、位图、光标、对话框、图标、菜单、字符串表和版本信息）的符号值必须是处于 0 到 32,767 的范围中的十进制数字（但不能为十六进制）。 资源的部件（如对话框控件或字符串表中的各个字符串）的符号值可以从 0 到 65,534 或从 -32,768 到 32,767。

资源符号是 16 位数字。 可以输入它们作为符号或无符号，但是，它们内部用作无符号整数。 因此负数会强制转换为对应的正数值。

下面是符号值的一些限制：

- Visual Studio 开发环境和 MFC 将一些数字范围用于特殊用途。 设置了最高有效位的所有数字（-32,768 到 -1，或 32,768 到 65,534，具体取决于符号）由 MFC 保留。

- 您不能定义使用其他符号字符串的符号值。 例如，不支持以下符号定义：

    ```cpp
    #define IDC_MYEDIT  IDC_OTHEREDIT  //not supported
    ```

- 您不能用作值定义参数使用预处理器宏。 例如：

    ```cpp
    #define   IDD_ABOUT  ID(7) //not supported
    ```

   不是有效的表达式，而不考虑什么`ID`在编译时计算的结果。

- 应用程序可能具有包含使用表达式定义的符号的现有文件。 有关如何包含符号作为只读符号的详细信息，请参阅[使用共享 （只读） 或计算符号](../windows/including-shared-read-only-or-calculated-symbols.md)。

有关数字范围的详细信息，请参阅[TN023:标准 MFC 资源](../mfc/tn023-standard-mfc-resources.md)。

### <a name="to-change-a-symbol-value"></a>若要更改符号值

1. 在中[资源视图](../windows/resource-view-window.md)，选择的资源。

1. 在中**属性**窗口中，键入符号名称后跟一个等号和中的整数**ID**框中，例如：

    ```
    IDC_EDITNAME=5100
    ```

下次保存项目时，新值会存储在符号头文件中。 中的 ID 框中; 只有符号名保持可见它们验证之后，不显示的等号和值。

## <a name="change-or-delete-unassigned-symbols"></a>更改或删除未赋值的符号

在处于[资源符号对话框](../windows/resource-symbols-dialog-box.md)，可以编辑或删除现有不已分配给资源或对象的符号。

### <a name="to-change-an-unassigned-symbol"></a>更改未分配的符号

1. 在中**名称**框中，选择未分配的符号，然后选择**更改**。

1. 中提供的框中编辑符号的名称或值**更改符号**对话框。

   > [!NOTE]
   > 若要更改符号的*是*分配给资源或对象，必须使用资源编辑器或**属性**窗口。

### <a name="to-delete-an-unassigned-unused-symbol"></a>删除未分配（未使用）的符号

在中[资源符号对话框](../windows/resource-symbols-dialog-box.md)，选择你想要删除，并且选择符号**删除**。

   > [!NOTE]
   > 在资源文件中删除未使用的符号之前，请确保它未在程序中的其他位置使用，也未由编译时包含的资源文件使用。

## <a name="include-shared-read-only-or-calculated-symbols"></a>包含共享 （只读） 或计算符号

开发环境首次读取由其他应用程序创建的资源文件时，会将所有包含的头文件都标记为只读。 尽管可以使用[资源包括对话框的](../windows/resource-includes-dialog-box.md)添加其他只读符号头文件。

可能要使用只读符号定义的原因之一是用于计划在多个项目之间共享的符号文件。

当现有资源包含的符号定义使用表达式而不是简单整数来定义符号值时，也可以使用包含的符号文件。 例如：

```cpp
#define   IDC_CONTROL1 2100
#define   IDC_CONTROL2 (IDC_CONTROL1+1)
```

只要满足以下条件，环境便会正确解释这些计算的符号：

- 计算的符号置于只读符号文件中。

- 资源文件包含已分配有这些计算的符号的资源。

- 需要数值表达式。

> [!NOTE]
> 如果需要字符串或数值表达式，则不会计算表达式。

### <a name="to-include-shared-read-only-symbols-in-your-resource-file"></a>在资源文件包含共享（只读）符号

1. 在中[资源视图](../windows/resource-view-window.md)，右键单击.rc 文件，然后选择[资源包括](../windows/resource-includes-dialog-box.md)从快捷菜单。

1. 在中**只读符号指令**框中，使用`#include`编译器指令，以指定想要保留只读符号的文件。

   请勿调用文件`Resource.h`，因为它是通常由主符号头文件的文件名。

   > [!NOTE]
   > **重要**完全按照您键入您在只读符号指令框中键入包含资源文件中。 请确保输入的内容不包含任何拼写或语法错误。

   使用**只读符号指令**框可包括仅限符号定义的文件。 不包含资源定义;否则，保存文件时，会创建重复的资源定义。

1. 将符号置于指定的文件中。

   在这种方式中包含的文件中的符号的计算每次打开资源文件中，但它们不是在磁盘上替换时保存您的文件。

1. 选择 **确定**。

### <a name="to-change-the-name-of-the-resource-symbol-header-file"></a>更改资源符号头文件的名称

1. 在中[资源视图](../windows/resource-view-window.md)，右键单击.rc 文件，然后选择[资源包括](../windows/resource-includes-dialog-box.md)从快捷菜单。

1. 在中**符号头文件**框中，键入包含文件的新名称。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[符号：资源标识符](../windows/symbols-resource-identifiers.md)<br/>
[预定义的符号 ID](../windows/predefined-symbol-ids.md)<br/>
[查看资源符号](../windows/viewing-resource-symbols.md)<br/>