---
title: 保留字
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
ms.openlocfilehash: 16caacb77e052eebc8e2cd101990ee373535bd6e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80171146"
---
# <a name="reserved-words"></a>保留字

链接器保留以下单词。 仅当名称括在双引号（""）中时，才可以将这些名称用作[module 定义语句](module-definition-dot-def-files.md)中的参数。

||||
|-|-|-|
|**APPLOADER**<sup>1</sup>|**INITINSTANCE**<sup>2</sup>|**预加载**|
|**基座**|**IOPL**|**专有**|
|**编写**|**库**<sup>1</sup>|**PROTMODE**<sup>2</sup>|
|**规范**|**LOADONCALL**<sup>1</sup>|**纯**<sup>1</sup>|
|**数据**|**LONGNAMES**<sup>2</sup>|**只读**|
|**DESCRIPTION**|**可移动**<sup>1</sup>|**READWRITE**|
|**DEV386**|**可移动**<sup>1</sup>|**REALMODE**<sup>1</sup>|
|**可放弃**|**多个**|**常驻**|
|**动态**|**NAME**|**RESIDENTNAME**<sup>1</sup>|
|**仅执行**|**Newfiles.format.ps1xml**<sup>2</sup>|**个**|
|**EXECUTEONLY**|**NODATA**<sup>1</sup>|**边**|
|**EXECUTEREAD**|**NOIOPL**<sup>1</sup>|**共享**|
|**EXETYPE**|**NONAME**|**单个**|
|**EXPORTS**|**NONCONFORMING**不符合<sup>1</sup>|**STACKSIZE**|
|**固定**<sup>1</sup>|**NONDISCARDABLE**|**STUB**|
|**函数**<sup>2</sup>|**NONE**|**VERSION**|
|**HEAPSIZE**|**非共享**|**WINDOWAPI**|
|**导**|**NOTWINDOWCOMPAT**<sup>1</sup>|**WINDOWCOMPAT**|
|**非纯**<sup>1</sup>|**对象**|**WINDOWS**|
|**包含**<sup>2</sup>|**旧**<sup>1</sup>||

<sup>1</sup>链接器在遇到此字词时发出警告（"忽略"）。 但仍保留该单词。

<sup>2</sup>链接器忽略此词，但不发出警告。

## <a name="see-also"></a>另请参阅

- [MSVC 链接器参考](linking.md)
- [MSVC 链接器选项](linker-options.md)
