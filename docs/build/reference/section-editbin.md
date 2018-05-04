---
title: -SECTION (EDITBIN) |Microsoft 文档
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
ms.openlocfilehash: e29e258b4fb661cfa06e057704bba983ad924f34
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="section-editbin"></a>/SECTION (EDITBIN)
```  
/SECTION:name[=newname][,attributes][alignment]  
```  
  
## <a name="remarks"></a>备注  
 此选项更改的部分中，重写节的对象文件已编译或链接时设置的属性的属性。  
  
 冒号后面 ( **:** )，指定*名称*的部分。 若要更改的部分名称，请按照*名称*以等号 （=） 和一个*newname*部分。  
  
 若要设置或更改的部分`attributes`，指定逗号 (**，**) 跟一个或多个属性字符。 要求反属性，其在字符前加感叹号 （！）。 以下字符指定内存特性：  
  
|特性|设置|  
|---------------|-------------|  
|c|代码|  
|d|可丢弃|  
|E|可执行文件|  
|i|初始化的数据|  
|k|缓存的虚拟内存|  
|m|链接删除|  
|o|链接信息|  
|p|虚拟内存分页|  
|r|读取|  
|秒|共享|  
|u|未初始化的数据|  
|w|写入|  
  
 控制*对齐*，指定的字符**A**跟将对齐的大小，如下所示设置以字节为单位，下列字符之一：  
  
|字符|对齐大小 （字节）|  
|---------------|-----------------------------|  
|1|1|  
|2|2|  
|4|4|  
|8|8|  
|p|16|  
|t|32|  
|秒|64|  
|x|不对齐|  
  
 指定`attributes`和*对齐*作为字符串的任何空格的字符。 这些字符不区分大小写。  
  
## <a name="see-also"></a>请参阅  
 [EDITBIN 选项](../../build/reference/editbin-options.md)