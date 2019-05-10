---
title: /RAWDATA
ms.date: 11/04/2016
f1_keywords:
- /rawdata
helpviewer_keywords:
- RAWDATA dumpbin option
- raw data
- -RAWDATA dumpbin option
- /RAWDATA dumpbin option
ms.assetid: 41cba845-5e1f-415e-9fe4-604a52235983
ms.openlocfilehash: 02af8df04d80c20c5d7629b51abab6295a21f5e5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62319507"
---
# <a name="rawdata"></a>/RAWDATA

```
/RAWDATA[:{1|2|4|8|NONE[,number]]
```

## <a name="remarks"></a>备注

此选项显示在文件中的每个部分的原始内容。 参数控制的格式显示，如下所示：

|参数|结果|
|--------------|------------|
|1|默认值。 如果他们有打印的表示形式，内容将显示以十六进制字节为单位，以及作为 ASCII 字符。|
|2|内容显示为十六进制的 2 字节值。|
|4|内容显示为 4 字节的十六进制值。|
|8|内容显示为 8 字节的十六进制值。|
|无|取消显示原始数据。 此参数可用于控制输出的/所有。|
|数字|显示的行设置为保留的宽度`number`每行的值。|

仅[/HEADERS](headers.md) DUMPBIN 选项仅适用于使用产生的文件[/GL](gl-whole-program-optimization.md)编译器选项。

## <a name="see-also"></a>请参阅

[DUMPBIN 选项](dumpbin-options.md)
