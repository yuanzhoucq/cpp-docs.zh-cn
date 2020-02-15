---
title: EDITBIN 选项
description: Microsoft EDITBIN 实用程序命令行选项的参考指南。
ms.date: 02/09/2020
f1_keywords:
- editbin
helpviewer_keywords:
- EDITBIN program, options
ms.assetid: 2da9f88e-cbab-4d64-bb66-ef700535230f
ms.openlocfilehash: c27172522ceabeccd06d7b957aa791edc49beec8
ms.sourcegitcommit: 8414cd91297dea88c480e208c7b5301db9972f19
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2020
ms.locfileid: "77257697"
---
# <a name="editbin-options"></a>EDITBIN 选项

您可以使用 EDITBIN 来修改对象文件、可执行文件和动态链接库（Dll）。 选项指定 EDITBIN 做的更改。

选项包括一个选项说明符，该说明符为短划线（`-`）或正斜杠（`/`），后跟选项的名称。 不能缩写选项名称。 某些选项采用冒号（`:`）之后指定的参数。 选项规范内不允许有空格或制表符。 在命令行上使用一个或多个空格或制表符分隔选项规范。 选项名及其关键字参数或文件名自变量不区分大小写。 例如，`-bind` 和 `/BIND` 表示相同的内容。

EDITBIN 具有以下选项：

|选项|目的|
|------------|-------------|
|[/ALLOWBIND](allowbind.md)|指定一个 DLL 是否可以绑定。|
|[/ALLOWISOLATION](allowisolation.md)|指定 DLL 或可执行文件清单查找行为。|
|[/APPCONTAINER](appcontainer.md)|指定应用程序是否必须在 AppContainer 内运行，例如 UWP 应用。|
|[/BIND](bind.md)|将指定对象中的入口点地址设为速度加载时间。|
|[/DYNAMICBASE](dynamicbase.md)|使用地址空间布局随机化 (ASLR) 功能，指定是否可在加载时随机重新设定 DLL 或可执行图像的基址。|
|[/ERRORREPORT](errorreport-editbin-exe.md)| 已弃用。 错误报告由[Windows 错误报告（WER）](/windows/win32/wer/windows-error-reporting)设置控制。 |
|[/HEAP](heap.md)|以字节设置可执行映像堆的大小。|
|[/HIGHENTROPYVA](highentropyva.md)|指定 DLL 或可执行映像是否支持高熵（64 位）地址空间布局随机化 (ASLR)。|
|[/INTEGRITYCHECK](integritycheck.md)|指定是否在加载时检查数字签名。|
|[/LARGEADDRESSAWARE](largeaddressaware.md)|指定对象是否支持大于 2 GB 的地址。|
|[/NOLOGO](nologo-editbin.md)|取消显示 EDITBIN 启动横幅。|
|[/NXCOMPAT](nxcompat.md)|指定可执行映像是否与 Windows 数据执行保护兼容。|
|[/REBASE](rebase.md)|设置指定对象的基址。|
|[/RELEASE](release.md)|在标头中设置校验和。|
|[/SECTION](section-editbin.md)|重写节的特性。|
|[/STACK](stack.md)|以字节设置可执行映像栈的大小。|
|[/SUBSYSTEM](subsystem.md)|指定执行环境。|
|[/SWAPRUN](swaprun.md)|指定可执行映像复制到交换文件，然后从该文件运行。|
|[/TSAWARE](tsaware.md)|指定应用可在多用户环境中运行。|
|[/VERSION](version.md)|在标头中设置版本号。|

## <a name="see-also"></a>另请参阅

[其他 MSVC 生成工具](c-cpp-build-tools.md)\
[EDITBIN 参考](editbin-reference.md)
