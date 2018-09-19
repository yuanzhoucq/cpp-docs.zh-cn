---
title: -SECTION (EDITBIN) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /section
dev_langs:
- C++
helpviewer_keywords:
- -SECTION editbin option
- SECTION editbin option
- alignment characters in sections
- /SECTION editbin option
ms.assetid: 4680ab4e-c984-4251-8241-93440cad7615
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3f91d467681d5a4d5bf4eaa5f042ef44b87810b3
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45701970"
---
# <a name="section-editbin"></a>/SECTION (EDITBIN)

```
/SECTION:name[=newname][,attributes][alignment]
```

## <a name="remarks"></a>备注

此选项可更改的部分中，重写部分中的对象文件已编译或链接时设置的属性的属性。

冒号后面 ( **:** )，指定*名称*的部分。 若要更改的部分名称，请按照*名称*以等号 （=） 和一个*newname*的部分。

若要设置或更改的部分`attributes`，指定逗号 (**，**) 后跟一个或多个属性的字符。 要求反属性，其在字符前加一个感叹号 （！）。 以下字符指定内存属性：

|特性|设置|
|---------------|-------------|
|c|代码|
|d|可放弃|
|E|可执行文件|
|i|已初始化的数据|
|k|虚拟内存缓存|
|m|删除链接|
|o|链接信息|
|p|虚拟内存分页|
|r|读取|
|秒|共享|
|u|未初始化的数据|
|w|写入|

控制*对齐*，指定的字符**A**后面要集对齐的大小 （字节），按如下所示的以下字符之一：

|字符|对齐大小 （字节）|
|---------------|-----------------------------|
|1|1|
|2|2|
|4|4|
|8|8|
|p|16|
|t|32|
|秒|64|
|x|未对齐|

指定`attributes`并*对齐*作为字符串的任何空格字符。 字符不区分大小写。

## <a name="see-also"></a>请参阅

[EDITBIN 选项](../../build/reference/editbin-options.md)