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
ms.openlocfilehash: 7d51f599dfb81dfa860e1bdba86c4372e80379fb
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57822439"
---
# <a name="reserved-words"></a>保留的字

链接器保留了下列关键字。 这些名称可用作中的自变量[模块定义语句](module-definition-dot-def-files.md)仅当名称括在双引号 ("")。

||||
|-|-|-|
|**APPLOADER**<sup>1</sup>|**INITINSTANCE**<sup>2</sup>|**预加载**|
|**BASE**|**IOPL**|**PRIVATE**|
|**CODE**|**LIBRARY**<sup>1</sup>|**PROTMODE**<sup>2</sup>|
|**符合**|**由**<sup>1</sup>|**纯**<sup>1</sup>|
|**DATA**|**LONGNAMES**<sup>2</sup>|**READONLY**|
|**说明**|**可移动**<sup>1</sup>|**READWRITE**|
|**DEV386**|**可移动**<sup>1</sup>|**REALMODE**<sup>1</sup>|
|**可放弃**|**多个**|**RESIDENT**|
|**DYNAMIC**|**NAME**|**RESIDENTNAME**<sup>1</sup>|
|**EXECUTE-ONLY**|**NEWFILES**<sup>2</sup>|**部分**|
|**EXECUTEONLY**|**NODATA**<sup>1</sup>|**SEGMENTS**|
|**EXECUTEREAD**|**NOIOPL**<sup>1</sup>|**SHARED**|
|**EXETYPE**|**NONAME**|**单个**|
|**EXPORTS**|**不一致**<sup>1</sup>|**STACKSIZE**|
|**固定**<sup>1</sup>|**NONDISCARDABLE**|**STUB**|
|**函数**<sup>2</sup>|**无**|**VERSION**|
|**HEAPSIZE**|**非共享**|**WINDOWAPI**|
|**导入**|**NOTWINDOWCOMPAT**<sup>1</sup>|**WINDOWCOMPAT**|
|**IMPURE**<sup>1</sup>|**OBJECTS**|**WINDOWS**|
|**包括**<sup>2</sup>|**OLD**<sup>1</sup>||

<sup>1</sup>链接器会发出警告 （"忽略"），当遇到此术语。 但是，一词是仍保留。

<sup>2</sup>链接器将忽略此单词，但是不发出警告。

## <a name="see-also"></a>请参阅

- [MSVC 链接器引用](linking.md)
- [MSVC 链接器选项](linker-options.md)