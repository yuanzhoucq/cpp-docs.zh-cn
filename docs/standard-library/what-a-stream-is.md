---
title: 流的定义
ms.date: 11/04/2016
helpviewer_keywords:
- reading data [C++], iostream programming
- data [C++], reading
- streams [C++], in iostream classes
- streams [C++]
ms.assetid: a7e661e9-6cd1-4543-a9a4-c58ee9fd32f3
ms.openlocfilehash: 80f2d17d7de2ddca1ef1501cacdb44f41c06594b
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68450942"
---
# <a name="what-a-stream-is"></a>流的定义

与 C 类似，C++ 不具有内置输入/输出功能。 但是，所有 C++ 编译器都捆绑了一个系统的、面向对象的 I/O 包，称为 iostream 类。 该流是 iostream 类中的核心概念。 可将流对象视为一个智能文件，此文件充当字节的源和目标。 流的特征由其类和自定义的插入和提取运算符确定。

通过设备驱动程序，磁盘操作系统可将键盘、屏幕、打印机和通信端口作为扩展文件来处理。 iostream 类与这些扩展文件进行交互。 内置类支持使用与磁盘 I/O 相同的语法写入内存或从中读取，从而可以轻松派生流类。

## <a name="in-this-section"></a>本节内容

[输入/输出替换选项](../standard-library/input-output-alternatives.md)

## <a name="see-also"></a>请参阅

[iostream 编程](../standard-library/iostream-programming.md)
