---
title: 输入流
ms.date: 11/04/2016
helpviewer_keywords:
- reading data [C++], from input streams
- data [C++], reading from input stream
- input streams
- input stream objects
ms.assetid: f14d8954-8f8c-4c3c-8b99-14ddb3683f94
ms.openlocfilehash: 0f56f5ffc8e61c0881eddbbd65e1c431b9219674
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62404918"
---
# <a name="input-streams"></a>输入流

输入流对象是字节的源。 三个最重要的输入流类分别是 [istream](../standard-library/basic-istream-class.md)、[ifstream](../standard-library/basic-ifstream-class.md) 和 [istringstream](../standard-library/basic-istringstream-class.md)。

`istream` 类最适合用于顺序文本模式输入。 可为缓冲操作或无缓冲操作配置 `istream` 类的对象。 基类 `ios` 的所有功能包含在 `istream` 中。 很少会从类 `istream` 构造对象。 相反，通常会使用预定义的 `cin` 对象，该对象实际上是 [ostream](../standard-library/basic-ostream-class.md) 类的对象。 某些情况下，在程序启动后可将 `cin` 分配给其他流对象。

`ifstream` 类支持磁盘文件输入。 如果需要只输入的磁盘文件，请构造 `ifstream` 类的对象。 可指定二进制或文本模式数据。 如果在构造函数中指定文件名，则在构造对象时会自动打开该文件。 另外，可在调用默认构造函数后使用 `open` 函数。 许多格式设置选项和成员函数适用于 `ifstream` 对象。 基类 `ios` 和 `istream` 的所有功能包含在 `ifstream` 中。

类似于库函数 `sscanf_s`，`istringstream` 类支持从内存中字符串进行输入。 若要从具有 null 终止符的字符组中提取数据，请分配并初始化字符串，然后构造 `istringstream` 类的对象。

## <a name="in-this-section"></a>本节内容

[构造输入流对象](../standard-library/constructing-input-stream-objects.md)

[使用提取运算符](../standard-library/using-extraction-operators.md)

[测试提取错误](../standard-library/testing-for-extraction-errors.md)

[输入流操控器](../standard-library/input-stream-manipulators.md)

[输入流成员函数](../standard-library/input-stream-member-functions.md)

[为自己的类重载 >> 运算符](../standard-library/overloading-the-input-operator-for-your-own-classes.md)

## <a name="see-also"></a>请参阅

[iostream 编程](../standard-library/iostream-programming.md)<br/>
