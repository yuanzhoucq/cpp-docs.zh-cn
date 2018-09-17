---
title: 部分 （C/C + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- SECTIONS
dev_langs:
- C++
helpviewer_keywords:
- SECTIONS .def file statement
ms.assetid: 7b974366-9ef5-4e57-bbcc-73a1df6f8857
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ecd8d6050df7a4d30b0a37cad28e030d1cd63cf0
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45722882"
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

较旧版本的 Visual c + + 支持：

```
section [CLASS 'classname'] specifier
```

`CLASS`关键字支持的兼容性，但被忽略。

指定节特性等效方法是使用[/section](../../build/reference/section-specify-section-attributes.md)选项。

## <a name="see-also"></a>请参阅

[模块定义语句的规则](../../build/reference/rules-for-module-definition-statements.md)