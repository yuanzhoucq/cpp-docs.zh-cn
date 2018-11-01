---
title: 保留的字
ms.date: 11/04/2016
f1_keywords:
- code
- CONFORMING
- DISCARDABLE
- Description
- base
- APPLOADER
- Data
- DYNAMIC
- DEV386
helpviewer_keywords:
- .def files [C++], reserved words
- def files [C++], reserved words
- linker [C++], reserved words
- reserved words [C++]
ms.assetid: 9b9f49e5-0739-45ab-a37e-81e3915ceb25
ms.openlocfilehash: 360baf479f9100483fe694ca8860dfc1d7ebfe11
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50502461"
---
# <a name="reserved-words"></a>保留的字

链接器保留了下列关键字。 这些名称可用作中的自变量[模块定义语句](../../build/reference/module-definition-dot-def-files.md)仅当名称括在双引号 ("")。

||||
|-|-|-|
|**APPLOADER**<sup>1</sup>|**INITINSTANCE**<sup>2</sup>|**预加载**|
|**基本**|**IOPL**|**专用**|
|**代码**|**库**<sup>1</sup>|**PROTMODE**<sup>2</sup>|
|**符合**|**由**<sup>1</sup>|**纯**<sup>1</sup>|
|**数据**|**LONGNAMES**<sup>2</sup>|**只读**|
|**说明**|**可移动**<sup>1</sup>|**READWRITE**|
|**DEV386**|**可移动**<sup>1</sup>|**实模式**<sup>1</sup>|
|**可放弃**|**多个**|**驻留在**|
|**动态**|**名称**|**RESIDENTNAME**<sup>1</sup>|
|**仅执行**|**NEWFILES**<sup>2</sup>|**部分**|
|**EXECUTEONLY**|**NODATA**<sup>1</sup>|**段**|
|**执行读取**|**NOIOPL**<sup>1</sup>|**共享**|
|**EXETYPE**|**NONAME**|**单个**|
|**EXPORTS**|**不一致**<sup>1</sup>|**STACKSIZE**|
|**固定**<sup>1</sup>|**NONDISCARDABLE**|**STUB**|
|**函数**<sup>2</sup>|**无**|**版本**|
|**HEAPSIZE**|**非共享**|**WINDOWAPI**|
|**导入**|**NOTWINDOWCOMPAT**<sup>1</sup>|**WINDOWCOMPAT**|
|**非纯**<sup>1</sup>|**对象**|**WINDOWS**|
|**包括**<sup>2</sup>|**旧**<sup>1</sup>||

<sup>1</sup>链接器会发出警告 （"忽略"），当遇到此术语。 但是，一词是仍保留。

<sup>2</sup>链接器将忽略此单词，但是不发出警告。

## <a name="see-also"></a>请参阅

- [设置链接器选项](../../build/reference/setting-linker-options.md)
- [链接器选项](../../build/reference/linker-options.md)