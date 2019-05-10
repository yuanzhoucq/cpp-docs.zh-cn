---
title: SECTIONS (C/C++)
ms.date: 11/04/2016
f1_keywords:
- SECTIONS
helpviewer_keywords:
- SECTIONS .def file statement
ms.assetid: 7b974366-9ef5-4e57-bbcc-73a1df6f8857
ms.openlocfilehash: 5125b09675969c784aafe375faf1fdbc36d8c5d9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62318623"
---
# <a name="sections-cc"></a>SECTIONS (C/C++)

引入了一个或多个部分`definitions`是对您的项目的输出文件中的分区的访问说明符。

```
SECTIONS
definitions
```

## <a name="remarks"></a>备注

每个定义必须在单独一行上。 `SECTIONS`关键字可以是第一个定义的同一行上或在前面的行。 .Def 文件可以包含一个或多个`SECTIONS`语句。

这`SECTIONS`语句图像文件中的一个或多个部分设置属性，并可用于重写节的每个类型的默认属性。

格式为`definitions`是：

`.section_name specifier`

其中`.section_name`是应用程序映像中的某个部分的名称和`specifier`是一个或多个以下访问修饰符：

|修饰符|描述|
|--------------|-----------------|
|`EXECUTE`|部分是可执行文件|
|`READ`|允许对数据的读取的操作|
|`SHARED`|将图像加载的所有进程之间共享该节|
|`WRITE`|允许对数据的写入操作|

请用空格分隔说明符的名称。 例如：

```
SECTIONS
.rdata READ WRITE
```

`SECTIONS` 表示一组部分的开头`definitions`。 每个`definition`必须位于一个单独的行上。 `SECTIONS`关键字可以是在同一行与第一个`definition`或在前面的行上。 .Def 文件可以包含一个或多个`SECTIONS`语句。 `SEGMENTS`的同义词支持关键字`SECTIONS`。

较旧版本的视觉对象C++支持：

```
section [CLASS 'classname'] specifier
```

`CLASS`关键字支持的兼容性，但被忽略。

指定节特性等效方法是使用[/section](section-specify-section-attributes.md)选项。

## <a name="see-also"></a>请参阅

[模块定义语句的规则](rules-for-module-definition-statements.md)
