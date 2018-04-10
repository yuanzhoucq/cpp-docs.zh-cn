---
title: 部分 （C/C + +） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SECTIONS
dev_langs:
- C++
helpviewer_keywords:
- SECTIONS .def file statement
ms.assetid: 7b974366-9ef5-4e57-bbcc-73a1df6f8857
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0ab2f021a53e8ae685891863500feb3873e13e2e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="sections-cc"></a>SECTIONS (C/C++)
引入了一个或多个部分`definitions`是对你的项目的输出文件中的分区的访问说明符。  
  
```  
SECTIONS  
definitions  
```  
  
## <a name="remarks"></a>备注  
 每个定义必须在单独一行上。 `SECTIONS`关键字可以在同一行的第一个定义或前一行上。 .Def 文件可以包含一个或多`SECTIONS`语句。  
  
 这`SECTIONS`语句中图像文件，一个或多个部分的设置属性，并可以用于重写每种类型的部分将默认属性。  
  
 格式`definitions`是：  
  
 `.section_name specifier`  
  
 其中`.section_name`是你的程序映像中的节的名称和`specifier`是一个或多个以下访问修饰符：  
  
|修饰符|描述|  
|--------------|-----------------|  
|`EXECUTE`|部分是可执行文件|  
|`READ`|允许对数据进行读的操作|  
|`SHARED`|加载图像的所有进程之间共享该节|  
|`WRITE`|允许对数据进行写操作|  
  
 请用空格分隔说明符名称。 例如:  
  
```  
SECTIONS  
.rdata READ WRITE  
```  
  
 `SECTIONS`标记的部分列表的开始`definitions`。 每个`definition`必须在单独一行上。 `SECTIONS`关键字可以出现在与第一个相同的行上`definition`或在前面的行上。 .Def 文件可以包含一个或多`SECTIONS`语句。 `SEGMENTS`关键字支持的同义词`SECTIONS`。  
  
 支持较旧版本的 Visual c + +:  
  
```  
section [CLASS 'classname'] specifier  
```  
  
 `CLASS`支持的兼容性，但忽略了关键字。  
  
 指定节特性等效方法是使用[/部分](../../build/reference/section-specify-section-attributes.md)选项。  
  
## <a name="see-also"></a>请参阅  
 [模块定义语句的规则](../../build/reference/rules-for-module-definition-statements.md)