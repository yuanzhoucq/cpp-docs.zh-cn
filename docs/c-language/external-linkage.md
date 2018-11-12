---
title: 外部链接
ms.date: 11/04/2016
helpviewer_keywords:
- linkage [C++], external
- external linkage, about external linkage
- external linkage
ms.assetid: a6f8ea69-b405-4cdd-bf12-ad5462b73183
ms.openlocfilehash: 87e9e16eb115df8d100450f7f0dc44961886ab20
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50466256"
---
# <a name="external-linkage"></a>外部链接

如果标识符的文件范围级别的第一个声明不使用 static 存储类说明符，则该对象具有外部链接。

如果函数标识符的声明没有 storage-class-specifier，则就像使用 storage-class-specifier `extern` 声明它一样准确确定其链接。 如果对象标识符的声明具有文件范围但没有 storage-class-specifier，则其链接为外部的。

具有外部链接的标识符的名称指定相同的函数或数据对象，这与具有外部连接的相同名称的任何其他声明一样。 这两个声明可以在同一个翻译单元中，也可以在不同的翻译单元中。 如果该对象或函数还具有全局生存期，则该对象或函数由整个程序共享。

## <a name="see-also"></a>请参阅

[使用 extern 指定链接](../cpp/using-extern-to-specify-linkage.md)