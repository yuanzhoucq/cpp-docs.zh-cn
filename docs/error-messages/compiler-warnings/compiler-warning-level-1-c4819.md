---
title: 编译器警告（等级 1）C4819
ms.date: 04/08/2019
f1_keywords:
- C4819
helpviewer_keywords:
- C4819
ms.assetid: c0316e85-249c-414d-9df0-622d077c6bc2
ms.openlocfilehash: d43b49d473e7113d8cdfb89aaa6e93045e13d0f7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62406309"
---
# <a name="compiler-warning-level-1-c4819"></a>编译器警告（等级 1）C4819

> 该文件包含无法出现在当前代码页的字符 (*数*)。 以 Unicode 格式保存该文件防止数据丢失。

编译 ANSI 源文件上使用不能表示文件中的所有字符的代码页的系统时，出现 C4819。

有几种方法，若要解决 C4819。 一种简单方式是删除有问题的字符，如果不需要它，例如，如果它是一条注释。 为支持你的源代码所使用的字符集的控制面板中，可以设置系统代码页。 可以使用 Unicode[转义序列](/cpp/c-language/escape-sequences)创建字符或字符串使用仅基本 ANSI 字符集在源代码中的设置。 最后，您可以使用一个签名，也称为一个字节顺序标记 (BOM) 以 Unicode 格式保存文件。

若要将文件保存为 Unicode 格式，在 Visual Studio 中，选择**文件** > **另存为**。 在中**将文件另存为**对话框框中，选择下拉列表上**保存**按钮，然后选择**编码保存**。 如果将保存到相同的文件名，您可能需要确认你想要替换的文件。 中**高级保存选项**对话框中，选择可以表示该文件中的所有字符编码-例如， **Unicode (utf-8 带签名)-代码页 65001**，然后选择**确定**。