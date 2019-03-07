---
title: 使用 DEF 文件导入
ms.date: 11/04/2016
helpviewer_keywords:
- importing DLLs [C++], DEF files
- def files [C++], importing with
- .def files [C++], importing with
- dllimport attribute [C++], DEF files
- DLLs [C++], DEF files
ms.assetid: aefdbf50-f603-488a-b0d7-ed737bae311d
ms.openlocfilehash: f6e553a85e6c17a3ea914365ad29ad5136e50629
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57424767"
---
# <a name="importing-using-def-files"></a>使用 DEF 文件导入

如果您选择使用 **__declspec （dllimport)** .def 文件，以及应更改.def 文件以使用代替常量的数据来减少不正确编码会引起问题的可能性：

```
// project.def
LIBRARY project
EXPORTS
   ulDataInDll   DATA
```

下表显示了原因。

|关键字|发出中的导入库|导出|
|-------------|---------------------------------|-------------|
|`CONSTANT`|`_imp_ulDataInDll`， `_ulDataInDll`|`_ulDataInDll`|
|`DATA`|`_imp_ulDataInDll`|`_ulDataInDll`|

使用 **__declspec （dllimport)** 同时列出了常量和`imp`版本和.lib DLL 中的未修饰的名称导入创建以允许在显式链接的库。 使用 **__declspec （dllimport)** 和数据列表只是`imp`版本的名称。

如果使用常量时，可以使用以下代码构造之一访问`ulDataInDll`:

```
__declspec(dllimport) ULONG ulDataInDll; /*prototype*/
if (ulDataInDll == 0L)   /*sample code fragment*/
```

\- 或 -

```
ULONG *ulDataInDll;      /*prototype*/
if (*ulDataInDll == 0L)  /*sample code fragment*/
```

但是，如果在.def 文件中使用数据，仅使用以下定义编译的代码可以访问该变量`ulDataInDll`:

```
__declspec(dllimport) ULONG ulDataInDll;

if (ulDataInDll == 0L)   /*sample code fragment*/
```

使用常量是更大风险，因为如果你忘记了使用额外级别的间接寻址，可能无法访问导入地址表指向的变量，该变量。 由于导入地址表当前通过只读的编译器和链接器，此类问题可能通常表现为访问冲突。

如果它发现的.def 文件中的常量来应对这种情况下，当前的 Visual c + + 链接器会发出警告。 使用常量的唯一的真正原因是如果您不能重新编译的头文件中未列出某些对象文件 **__declspec （dllimport)** 原型上。

## <a name="see-also"></a>请参阅

[导入到应用程序中](../build/importing-into-an-application.md)
