---
title: 创建自己的对话框类
ms.date: 11/04/2016
helpviewer_keywords:
- dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
- files [MFC], creating
- dialog classes [MFC], Add Class Wizard
- dialog classes [MFC], creating
ms.assetid: d5321741-da41-47a8-bb1c-6a0e8b28c4c1
ms.openlocfilehash: bacedc49fcdabdd5dc7fb0f392a66afd3baadd06
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62241752"
---
# <a name="creating-your-dialog-class"></a>创建自己的对话框类

对于在程序中每个对话框中，创建新的对话框类以使用对话框资源。

[添加类](../ide/adding-a-class-visual-cpp.md)介绍了如何创建一个新的对话框类。 当使用添加类向导创建对话框类时，它将写入以下各项。H 和。您指定的 CPP 文件：

在。H 文件：

- 对话框类的类声明。 类派生自[CDialog](../mfc/reference/cdialog-class.md)。

在。CPP 文件：

- 消息映射的类。

- 对话框中的标准构造函数。

- 重写[DoDataExchange](../mfc/reference/cwnd-class.md#dodataexchange)成员函数。 编辑此函数。 它可用于对话框数据交换和验证功能，更高版本中所述[对话框数据交换和验证](../mfc/dialog-data-exchange-and-validation.md)。

## <a name="see-also"></a>请参阅

[使用代码向导创建对话框类](../mfc/creating-a-dialog-class-with-code-wizards.md)<br/>
[对话框的生命周期](../mfc/life-cycle-of-a-dialog-box.md)
