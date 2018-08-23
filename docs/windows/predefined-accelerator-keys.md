---
title: 预定义快捷键 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.accelerator
dev_langs:
- C++
helpviewer_keywords:
- accelerator keys
- keyboard shortcuts
- keyboard shortcuts, predefined
ms.assetid: f234c5f2-4ec3-4c9e-834a-b5dd297625b9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3f5ed6d95b48a4ecbe2fa23a377d8aac7a73feb9
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42603788"
---
# <a name="predefined-accelerator-keys"></a>预定义快捷键

有多个预定义快捷键，它们可能是 Windows 应用程序项目的一部分。 部分虚拟键适用于 Windows 环境。 其他支持的浏览器或 Unicode 应用程序。 你可以在任何快捷键中使用这些键。

|键|描述|
|---------|-----------------|
|VK_ACCEPT|IME 接受|
|VK_BROWSER_BACK|Windows：浏览器后退键|
|VK_BROWSER_FAVORITES|Windows：浏览器收藏键|
|VK_BROWSER_FORWARD|Windows：浏览器前进键|
|VK_BROWSER_HOME|Windows：浏览器开始和主页键|
|VK_BROWSER_REFRESH|Windows：浏览器刷新键|
|VK_BROWSER_SEARCH|Windows：浏览器搜索键|
|VK_BROWSER_STOP|Windows：浏览器停止键|
|VK_CONVERT|IME 转换|
|VK_FINAL|IME 最终模式|
|VK_HANGUEL|IME Hanguel 模式（为兼容性而保留；使用 VK_HANGUL）|
|VK_HANGUL|IME Hanguel 模式|
|VK_HANJA|IME Hanja 模式|
|VK_JUNJA|IME Junja 模式|
|VK_KANA|IME Kana 模式|
|VK_KANJI|IME Kanji 模式|
|VK_LAUNCH_APP1|Windows：开始应用程序 1 键|
|VK_LAUNCH_APP2|Windows：开始应用程序 2 键|
|VK_LAUNCH_MAIL|Windows：开始邮件键|
|VK_LAUNCH_MEDIA_SELECT|Windows：选择媒体键|
|VK_LCONTROL|左 Ctrl 键|
|VK_LMENU|左菜单键|
|VK_LSHIFT|左 SHIFT 键|
|VK_MEDIA_NEXT_TRACK|Windows：下一曲目键|
|VK_MEDIA_PLAY_PAUSE|Windows：播放/暂停媒体键|
|VK_MEDIA_PREV_TRACK|Windows：上一曲目键|
|VK_MEDIA_STOP|Windows：暂停媒体键|
|VK_MODECHANGE|IME 模式更改请求|
|VK_NONCONVERT|IME 不转换|
|VK_OEM_1|Windows：适用于美国标准键盘，“;:”键|
|VK_OEM_102|Windows：尖括号键或 RT 102 键键盘上的反斜杠键|
|VK_OEM_2|Windows： 适用于美国标准键盘，/？ 密钥|
|VK_OEM_3|Windows：适用于美国标准键盘，“`~”键|
|VK_OEM_4|Windows：适用于美国标准键盘，“[{”键|
|VK_OEM_5|Windows： 适用于美国标准键盘，\\&#124;键|
|VK_OEM_6|Windows：适用于美国标准键盘，“]}”键|
|VK_OEM_7|Windows：适用于美国标准键盘，“单引号/双引号”键|
|VK_OEM_COMMA|Windows：适用于美国标准键盘，“,”键|
|VK_OEM_MINUS|Windows：适用于任何国家/地区，“-”键|
|VK_OEM_PERIOD|Windows：适用于任何国家/地区，“.”键|
|VK_OEM_PLUS|Windows：适用于任何国家/地区，“.+”键|
|VK_PACKET|Windows：适用于传递 Unicode 字符，就如同它们是击键一样。|
|VK_RCONTROL|右 Ctrl 键|
|VK_RMENU|右菜单键|
|VK_RSHIFT|右 SHIFT 键|
|VK_SLEEP|计算机休眠键|
|VK_VOLUME_DOWN|Windows：音量降低键|
|VK_VOLUME_MUTE|Windows：音量静音键|
|VK_VOLUME_UP|Windows：音量增大键|
|VK_XBUTTON1|Windows：X1 鼠标按钮|
|VK_XBUTTON2|Windows：X2 鼠标按钮|

有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[快捷键编辑器](../windows/accelerator-editor.md)  
[资源编辑器](../windows/resource-editors.md)