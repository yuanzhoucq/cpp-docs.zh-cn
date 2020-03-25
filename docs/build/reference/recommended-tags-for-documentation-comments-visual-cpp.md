---
title: 建议用于文档注释的标记C++ （文档注释）
ms.date: 11/04/2016
ms.assetid: 6548e798-5235-4a38-9482-bdc7b88f40a9
ms.openlocfilehash: 4e0937b79012f65ba136e18ac81f014be23688f8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168858"
---
# <a name="recommended-tags-for-documentation-comments"></a>建议的文档注释标记

MSVC 编译器将处理代码中的文档注释，并为每个编译单位创建一个 .xdc 文件，而 xdcmake 会将 .xdc 文件处理为 .xml 文件。 处理 .xml 文件以创建文档需要在站点上细致地进行。

在类型和类型成员等构造中处理标记。

标记必须紧跟类型或成员。

> [!NOTE]
>  文档注释不能应用于命名空间或者位于属性和事件的非常规定义上；文档注释必须位于类中声明上。

编译器将处理属于有效 XML 形式的任何标记。 下列标记提供用户文档中的常用功能：

||||
|-|-|-|
|[\<c>](c-visual-cpp.md)|[\<code>](code-visual-cpp.md)|[\<example>](example-visual-cpp.md)|
|[\<exception>](exception-visual-cpp.md)1|[\<include>](include-visual-cpp.md)1|[\<list>](list-visual-cpp.md)|
|[\<para>](para-visual-cpp.md)|[\<param>](param-visual-cpp.md)1|[\<paramref>](paramref-visual-cpp.md)1|
|[\<permission>](permission-visual-cpp.md)1|[\<remarks>](remarks-visual-cpp.md)|[\<returns>](returns-visual-cpp.md)|
|[\<see>](see-visual-cpp.md)1|[\<seealso>](seealso-visual-cpp.md)1|[\<summary>](summary-visual-cpp.md)|
|[\<value>](value-visual-cpp.md)|||

1. 编译器将验证语法。

在当前版本中，MSVC 编译器不支持 `<paramref>`，这是其他 Visual Studio 编译器支持的标记。 Visual C++ 可能会在未来的版本中支持 `<paramref>`。

## <a name="see-also"></a>另请参阅

[XML 文档](xml-documentation-visual-cpp.md)
