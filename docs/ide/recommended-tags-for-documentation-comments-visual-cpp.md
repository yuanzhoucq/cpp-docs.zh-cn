---
title: 建议用于文档注释的标记 (Visual C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 6548e798-5235-4a38-9482-bdc7b88f40a9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2b48b93b6134d0618e80552752c18beb1f03f689
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46418289"
---
# <a name="recommended-tags-for-documentation-comments-visual-c"></a>建议用于文档注释的标记 (Visual C++)

Visual C++ 编译器将在代码中处理文档注释并为每个编译单位创建 .xdc 文件，而 xdcmake.exe 会将 .xdc 文件处理为 .xml 文件。 处理 .xml 文件以创建文档需要在站点上细致地进行。

在类型和类型成员等构造中处理标记。

标记必须紧跟类型或成员。

> [!NOTE]
>  文档注释不能应用于命名空间或者位于属性和事件的非常规定义上；文档注释必须位于类中声明上。

编译器将处理属于有效 XML 形式的任何标记。 下列标记提供用户文档中的常用功能：

||||
|-|-|-|
|[\<c>](../ide/c-visual-cpp.md)|[\<code>](../ide/code-visual-cpp.md)|[\<example>](../ide/example-visual-cpp.md)|
|[\<exception>](../ide/exception-visual-cpp.md)1|[\<include>](../ide/include-visual-cpp.md)1|[\<list>](../ide/list-visual-cpp.md)|
|[\<para>](../ide/para-visual-cpp.md)|[\<param>](../ide/param-visual-cpp.md)1|[\<paramref>](../ide/paramref-visual-cpp.md)1|
|[\<permission>](../ide/permission-visual-cpp.md)1|[\<remarks>](../ide/remarks-visual-cpp.md)|[\<returns>](../ide/returns-visual-cpp.md)|
|[\<see>](../ide/see-visual-cpp.md)1|[\<seealso>](../ide/seealso-visual-cpp.md)1|[\<summary>](../ide/summary-visual-cpp.md)|
|[\<value>](../ide/value-visual-cpp.md)|||

1. 编译器将验证语法。

在当前版本中，Visual C++ 编译器不支持 `<paramref>`，这是由其他 Visual Studio 编译器支持的标记。 Visual C++ 可能会在未来的版本中支持 `<paramref>`。

## <a name="see-also"></a>请参阅

[XML 文档](../ide/xml-documentation-visual-cpp.md)