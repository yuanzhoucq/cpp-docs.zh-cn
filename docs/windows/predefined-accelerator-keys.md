---
title: 快捷键（C++）
ms.date: 02/14/2019
helpviewer_keywords:
- accelerator keys
- keyboard shortcuts
- keyboard shortcuts [C++], predefined
- menus [C++], shortcut keys
- keyboard shortcuts [C++], menu association
ms.assetid: f234c5f2-4ec3-4c9e-834a-b5dd297625b9
ms.openlocfilehash: beb4e878138da3dc2905c86e18fedc658d7ceecf
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80215145"
---
# <a name="accelerator-keys-c"></a>快捷键（C++）

## <a name="predefined-accelerator-keys"></a>预定义快捷键

有多个预定义快捷键，它们可能是 Windows 应用程序项目的一部分。 部分虚拟键适用于 Windows 环境。 其他支持浏览器或 Unicode 应用程序。 你可以在任何快捷键中使用这些键。

|密钥|说明|
|---------|-----------------|
|VK_ACCEPT|（IME） accept|
|VK_BROWSER_BACK|Windows浏览器，**后退**键|
|VK_BROWSER_FAVORITES|Windows浏览器，**收藏夹**键|
|VK_BROWSER_FORWARD|Windows浏览器、**前进**键|
|VK_BROWSER_HOME|Windows浏览器、**启动**和**Home**键|
|VK_BROWSER_REFRESH|Windows浏览器，**刷新**密钥|
|VK_BROWSER_SEARCH|Windows浏览器，**搜索**键|
|VK_BROWSER_STOP|Windows浏览器，**停止**键|
|VK_CONVERT|（IME）转换|
|VK_FINAL|（IME）最终模式|
|VK_HANGUEL|中文Hanguel 模式（为兼容性而维护，请使用 VK_HANGUL）|
|VK_HANGUL|中文朝鲜文字模式|
|VK_HANJA|中文朝鲜语|
|VK_JUNJA|中文Junja 模式|
|VK_KANA|中文假名模式|
|VK_KANJI|中文日本汉字模式|
|VK_LAUNCH_APP1|Windows**启动应用程序 1**键|
|VK_LAUNCH_APP2|Windows**启动应用程序 2**键|
|VK_LAUNCH_MAIL|Windows**启动邮件**键|
|VK_LAUNCH_MEDIA_SELECT|Windows**选择媒体**密钥|
|VK_LCONTROL|**左 Ctrl**键|
|VK_LMENU|**左菜单**键|
|VK_LSHIFT|**左 Shift**键|
|VK_MEDIA_NEXT_TRACK|Windows**下一曲目**键|
|VK_MEDIA_PLAY_PAUSE|Windows**播放/暂停媒体**密钥|
|VK_MEDIA_PREV_TRACK|Windows**上一个曲目**键|
|VK_MEDIA_STOP|Windows**停止媒体**密钥|
|VK_MODECHANGE|（IME）模式更改请求|
|VK_NONCONVERT|（IME） nonconvert|
|VK_OEM_1|Windows对于美国标准键盘，为 **;：** key|
|VK_OEM_102|WindowsRT 102 键键盘上的尖括号键或反斜杠键|
|VK_OEM_2|Windows对于美国标准键盘， **/？** key|
|VK_OEM_3|Windows对于美国标准键盘， **`~** 键|
|VK_OEM_4|Windows对于美国标准键盘， **[{** key|
|VK_OEM_5|Windows对于美国标准键盘， **\\&#124;** 键|
|VK_OEM_6|Windows对于美国标准键盘，为 **]}** 键|
|VK_OEM_7|Windows对于美国标准键盘，"单引号/双引号" 键|
|VK_OEM_COMMA|Windows对于任何国家/地区， **，** 密钥|
|VK_OEM_MINUS|Windows对于任何国家/地区， **-** 密钥|
|VK_OEM_PERIOD|Windows对于任何国家/地区，为 **。** key|
|VK_OEM_PLUS|Windows对于任何国家/地区， **+** 密钥|
|VK_PACKET|Windows用于将 Unicode 字符作为键击传递。|
|VK_RCONTROL|**右 Ctrl**键|
|VK_RMENU|**右菜单**键|
|VK_RSHIFT|**右移**键|
|VK_SLEEP|**计算机睡眠**键|
|VK_VOLUME_DOWN|Windows调**低音量**键|
|VK_VOLUME_MUTE|Windows**音量静音**键|
|VK_VOLUME_UP|Windows调**高音量**键|
|VK_XBUTTON1|Windows**X1**鼠标按钮|
|VK_XBUTTON2|Windows**X2**鼠标按钮|

## <a name="accelerator-key-association"></a>加速键关联

很多时候，你希望某一菜单项和某一键盘组合可以发出相同的程序命令。 要执行此操作，可将相同的资源标识符（ID）分配给菜单项，并分配给应用程序的快捷键对应表中的条目。 接着你可以编辑该菜单项的标题，以显示快捷键的名称。 有关菜单项和快捷键的详细信息，请参阅[菜单命令](../windows/associating-a-menu-command-with-an-accelerator-key.md)。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>另请参阅

[快捷键编辑器](../windows/accelerator-editor.md)<br/>
