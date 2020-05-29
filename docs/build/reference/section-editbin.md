---
title: /SECTION (EDITBIN)
ms.date: 11/04/2016
f1_keywords:
- /section_editbin
helpviewer_keywords:
- -SECTION editbin option
- SECTION editbin option
- alignment characters in sections
- /SECTION editbin option
ms.assetid: 4680ab4e-c984-4251-8241-93440cad7615
ms.openlocfilehash: 770e1d1c1cf288a7fe68f5bd076791d43f5b8572
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79438914"
---
# <a name="section-editbin"></a>/SECTION (EDITBIN)

```
/SECTION:name[=newname][,attributes][alignment]
```

## <a name="remarks"></a>备注

此选项将更改节的特性，并覆盖在编译或链接节的对象文件时设置的特性。

在冒号（ **：** ）之后指定节的*名称*。 若要更改节名称，请在*名称*后跟一个等号（=）和节的*newname* 。

若要设置或更改节的 `attributes`，请指定一个逗号（ **，** ），后跟一个或多个属性字符。 若要对某个属性求反，请在其字符前面加上一个惊叹号（！）。 以下字符指定内存属性：

|属性|设置|
|---------------|-------------|
|c|代码|
|d|可放弃|
|e|可执行文件 (executable)|
|i|初始化数据|
|k|缓存的虚拟内存|
|m|链接删除|
|o|链接信息|
|p|分页虚拟内存|
|r|读取|
|s|共享|
|u|未初始化数据|
|w|write|

若要控制*对齐方式*，请指定字符**A**后跟以下字符之一以设置对齐大小（以字节为单位），如下所示：

|字符|对齐大小（字节）|
|---------------|-----------------------------|
|1|1|
|2|2|
|4|4|
|8|8|
|p|16|
|t|32|
|s|64|
|x|无对齐方式|

将 `attributes` 和*对齐*字符指定为不带空格的字符串。 字符不区分大小写。

## <a name="see-also"></a>另请参阅

[EDITBIN 选项](editbin-options.md)
