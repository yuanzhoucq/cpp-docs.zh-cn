---
title: 工具栏 （c + +） 上的按钮之间插入间隔 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Toolbar editor [C++], spacing toolbar buttons
- toolbar buttons [C++], space between buttons
ms.assetid: 4925ea6b-5d3a-4949-a920-bf371a37e529
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c4c205d6f800682cb67749a73f57b1c35d03de61
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46397437"
---
# <a name="inserting-a-space-between-buttons-on-a-toolbar-c"></a>工具栏 （c + +） 上的按钮之间插入间隔

一般情况下，要插入按钮之间有空格，只需将它们从另一个在工具栏上。 若要删除空间，请将它们拖向彼此。

### <a name="to-insert-a-space-before-a-button-that-is-not-followed-by-a-space"></a>若要不跟一个空格的按钮前插入空格

1. 将按钮拖动到右或向下直到与下一步按钮重叠大约一半。

### <a name="to-insert-a-space-before-a-button-which-is-followed-by-a-space-and-to-retain-that-trailing-space"></a>要插入的按钮之后的空格前的空间，并保留该尾随空格

1. 拖动按钮，直到右侧或底部边缘刚好接触下一步按钮，或只是重叠。

### <a name="to-insert-a-space-before-a-button-that-is-followed-by-a-space-and-close-up-that-following-space"></a>若要前插入空格跟一个空格的按钮并关闭该以下空间

1. 将按钮拖动到右或向下直到与下一步按钮重叠大约一半。

有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的托管应用中的资源的信息，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>要求

MFC 或 ATL

## <a name="see-also"></a>请参阅

[创建、移动和编辑工具栏按钮](../windows/creating-moving-and-editing-toolbar-buttons.md)<br/>
[工具栏编辑器](../windows/toolbar-editor.md)