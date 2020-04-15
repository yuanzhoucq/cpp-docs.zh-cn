---
title: 文档注释的建议标签（C++文档注释）
ms.date: 11/04/2016
ms.assetid: 6548e798-5235-4a38-9482-bdc7b88f40a9
ms.openlocfilehash: 1648d0eb019a3aad25641d7f6a7edd1ba26acf7e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336174"
---
# <a name="recommended-tags-for-documentation-comments"></a>建议的文档注释标记

MSVC 编译器将处理代码中的文档注释，并为每个编译和创建一个 .xdc 文件，xdcmake.exe 将处理 .xdc 文件到 .xml 文件。 处理 .xml 文件以创建文档需要在站点上细致地进行。

在类型和类型成员等构造中处理标记。

标记必须紧跟类型或成员。

> [!NOTE]
> 文档注释不能应用于命名空间或者位于属性和事件的非常规定义上；文档注释必须位于类中声明上。

编译器将处理属于有效 XML 形式的任何标记。 下列标记提供用户文档中的常用功能：

||||
|-|-|-|
|[\<c>](c-visual-cpp.md)|[\<代码>](code-visual-cpp.md)|[\<示例>](example-visual-cpp.md)|
|例外>1 [ \< ](exception-visual-cpp.md)|包括>1 [ \< ](include-visual-cpp.md)|[\<列表>](list-visual-cpp.md)|
|[\<第>段](para-visual-cpp.md)|参数>1 [ \< ](param-visual-cpp.md)|[ \<>](paramref-visual-cpp.md)1|
|权限>1 [ \< ](permission-visual-cpp.md)|[\<评论>](remarks-visual-cpp.md)|[\<返回>](returns-visual-cpp.md)|
|参见>1 [ \< ](see-visual-cpp.md)|另见>1 [ \< ](seealso-visual-cpp.md)|[\<摘要>](summary-visual-cpp.md)|
|[\<值>](value-visual-cpp.md)|||

1. 编译器将验证语法。

在当前版本中，MSVC 编译器不支持`<paramref>`，该标记由其他 Visual Studio 编译器支持。 Visual C++ 可能会在未来的版本中支持 `<paramref>`。

## <a name="see-also"></a>另请参阅

[XML 文档](xml-documentation-visual-cpp.md)
