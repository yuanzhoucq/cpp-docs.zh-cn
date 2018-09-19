---
title: 字节和宽流 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- Byte and Wide Streams
dev_langs:
- C++
helpviewer_keywords:
- byte streams
- wide streams
ms.assetid: 61ef0587-4cbc-4eb8-aae5-4c298dbbc6f9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e031aa0ebbad279c630f2687457af11dc478b72d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46095828"
---
# <a name="byte-and-wide-streams"></a>字节和宽流

字节流将文件视作一个字节序列。 在程序中，字节流是相同的字节序列。

相比之下，宽流将文件视作一个通用的多字节字符序列，可以具有广泛的编码规则。 （文本和二进制文件仍然如前所述进行读取和写入。）在程序中，宽流看起来像相应的宽字符序列。 两种表示形式之间的转换发生在标准 C 库中。 原则上，转换规则可以通过调用更改类别 `LC_CTYPE` 的 [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) 进行更改。 每个宽流在其变为面向宽度时确定其转换规则，并且即使类别 `LC_CTYPE` 随后发生更改也会保留这些规则。

在宽流中进行定位会受到与文本流相同的限制。 此外，文件位置指示器可能必须处理依赖于状态的编码。 通常，它包含流内的字节偏移量和 `mbstate_t` 类型的对象。 因此，获取宽流中的文件位置的唯一可靠方法是调用 [fgetpos](../c-runtime-library/reference/fgetpos.md)，并且还原以这种方法获得的位置的唯一可靠方法是调用 [fsetpos](../c-runtime-library/reference/fsetpos.md)。

## <a name="see-also"></a>请参阅

[文件和流](../c-runtime-library/files-and-streams.md)<br/>
[setlocale、_wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)