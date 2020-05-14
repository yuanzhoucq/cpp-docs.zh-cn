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
ms.openlocfilehash: 13a6a375d6200f73dd9845d057d1954c2b65485c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62273412"
---
# <a name="importing-using-def-files"></a>使用 DEF 文件导入

如果选择将“__declspec(dllimport)”与 .def 文件一起使用，则应将 .def 文件更改为使用 DATA 代替 CONSTANT，以降低错误编码导致问题的可能性  ：

```
// project.def
LIBRARY project
EXPORTS
   ulDataInDll   DATA
```

下表说明了原因。

|关键字|在导入库中发出|导出|
|-------------|---------------------------------|-------------|
|`CONSTANT`|`_imp_ulDataInDll`，`_ulDataInDll`|`_ulDataInDll`|
|`DATA`|`_imp_ulDataInDll`|`_ulDataInDll`|

使用“__declspec(dllimport)”和 CONSTANT 可列出为允许显式链接而创建的 .lib DLL 导入库中的 `imp` 版本和未修饰名  。 使用“__declspec(dllimport)”和 DATA 只能列出名称的 `imp` 版本  。

如果使用 CONSTANT，则可以使用以下任一代码构造来访问 `ulDataInDll`：

```
__declspec(dllimport) ULONG ulDataInDll; /*prototype*/
if (ulDataInDll == 0L)   /*sample code fragment*/
```

\- 或 -

```
ULONG *ulDataInDll;      /*prototype*/
if (*ulDataInDll == 0L)  /*sample code fragment*/
```

但如果使用 .def 文件中的 DATA，则只有使用下面的定义编译的代码才能访问变量 `ulDataInDll`：

```
__declspec(dllimport) ULONG ulDataInDll;

if (ulDataInDll == 0L)   /*sample code fragment*/
```

使用 CONSTANT 的风险更大，因为如果忘记使用额外级别的间接寻找，则访问的有可能是指向变量的导入地址表的指针，而不是变量本身。 由于导入地址表当前被编译器和链接器设置成了只读，因此这类问题经常表现为访问冲突。

如果当前 MSVC 链接器发现 .def 文件中的 CONSTANT 是导致上述问题的原因，它将发出警告。 使用 CONSTANT 的唯一真正原因是：无法对头文件未在原型上列出“__declspec(dllimport)”的某个对象文件进行重新编译  。

## <a name="see-also"></a>请参阅

[导入到应用程序中](importing-into-an-application.md)
