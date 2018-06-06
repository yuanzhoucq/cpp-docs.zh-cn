---
title: 保留字 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- .def files [C++], reserved words
- def files [C++], reserved words
- linker [C++], reserved words
- reserved words [C++]
ms.assetid: 9b9f49e5-0739-45ab-a37e-81e3915ceb25
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 132bd8e5ba66cbf9486a6da4747994c667e2f6e7
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2018
ms.locfileid: "34705655"
---
# <a name="reserved-words"></a>保留的字

链接器将保留下列词语。 这些名称可用作自变量中[模块定义语句](../../build/reference/module-definition-dot-def-files.md)仅当名称括在双引号 ("")。

||||
|-|-|-|
|**APPLOADER**<sup>1</sup>|**INITINSTANCE**<sup>2</sup>|**预加载**|
|**基**|**IOPL**|**私有**|
|**代码**|**库**<sup>1</sup>|**PROTMODE**<sup>2</sup>|
|**符合**|**由**<sup>1</sup>|**纯**<sup>1</sup>|
|**数据**|**LONGNAMES**<sup>2</sup>|**READONLY**|
|**说明**|**可移动**<sup>1</sup>|**READWRITE**|
|**DEV386**|**可移动**<sup>1</sup>|**实模式**<sup>1</sup>|
|**可丢弃**|**多个**|**驻留**|
|**动态**|**名称**|**RESIDENTNAME**<sup>1</sup>|
|**仅执行**|**NEWFILES**<sup>2</sup>|**部分**|
|**EXECUTEONLY**|**无数据**<sup>1</sup>|**段**|
|**执行读取**|**NOIOPL**<sup>1</sup>|**共享**|
|**EXETYPE**|**NONAME**|**单个**|
|**EXPORTS**|**不一致性**<sup>1</sup>|**STACKSIZE**|
|**固定**<sup>1</sup>|**NONDISCARDABLE**|**STUB**|
|**函数**<sup>2</sup>|**无**|**版本**|
|**HEAPSIZE**|**非共享**|**WINDOWAPI**|
|**导入**|**NOTWINDOWCOMPAT**<sup>1</sup>|**WINDOWCOMPAT**|
|**非纯**<sup>1</sup>|**对象**|**WINDOWS**|
|**包括**<sup>2</sup>|**旧**<sup>1</sup>||

<sup>1</sup>遇到此术语时，链接器将发出警告 （"忽略"）。 但是，单词是仍保留。

<sup>2</sup>链接器忽略该保留字，但是不发出警告。

## <a name="see-also"></a>请参阅

- [设置链接器选项](../../build/reference/setting-linker-options.md)
- [链接器选项](../../build/reference/linker-options.md)