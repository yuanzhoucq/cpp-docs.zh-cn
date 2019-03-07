---
title: 加速键 （c + +）
ms.date: 02/14/2019
f1_keywords:
- vc.editors.accelerator
helpviewer_keywords:
- accelerator keys
- keyboard shortcuts
- keyboard shortcuts [C++], predefined
- menus [C++], shortcut keys
- keyboard shortcuts [C++], menu association
ms.assetid: f234c5f2-4ec3-4c9e-834a-b5dd297625b9
ms.openlocfilehash: 99867f146ca80d8b48c9be9deb59044207b33af1
ms.sourcegitcommit: e06648107065f3dea35f40c1ae5999391087b80b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/01/2019
ms.locfileid: "57210492"
---
# <a name="accelerator-keys-c"></a>加速键 （c + +）

## <a name="predefined-accelerator-keys"></a>预定义快捷键

有多个预定义快捷键，它们可能是 Windows 应用程序项目的一部分。 部分虚拟键适用于 Windows 环境。 其他支持浏览器或 Unicode 应用程序。 你可以在任何快捷键中使用这些键。

|键|描述|
|---------|-----------------|
|VK_ACCEPT|(IME) 接受|
|VK_BROWSER_BACK|(Windows)浏览器中，**回**密钥|
|VK_BROWSER_FAVORITES|(Windows)浏览器中，**收藏夹**密钥|
|VK_BROWSER_FORWARD|(Windows)浏览器中，**转发**密钥|
|VK_BROWSER_HOME|(Windows)浏览器中，**启动**并**主页**密钥|
|VK_BROWSER_REFRESH|(Windows)浏览器中，**刷新**密钥|
|VK_BROWSER_SEARCH|(Windows)浏览器中，**搜索**密钥|
|VK_BROWSER_STOP|(Windows)浏览器中，**停止**密钥|
|VK_CONVERT|(IME) 转换|
|VK_FINAL|(IME) 最终模式|
|VK_HANGUEL|(IME)Hanguel 模式 （为了保持兼容，使用 VK_HANGUL）|
|VK_HANGUL|(IME)朝鲜文模式|
|VK_HANJA|(IME)朝鲜文汉字模式|
|VK_JUNJA|(IME)Junja 模式|
|VK_KANA|(IME)Kana 模式|
|VK_KANJI|(IME)Kanji 模式|
|VK_LAUNCH_APP1|(Windows)**启动应用程序 1**密钥|
|VK_LAUNCH_APP2|(Windows)**启动应用程序 2**密钥|
|VK_LAUNCH_MAIL|(Windows)**启动邮件**密钥|
|VK_LAUNCH_MEDIA_SELECT|(Windows)**选择媒体**密钥|
|VK_LCONTROL|**左 Ctrl**密钥|
|VK_LMENU|**左菜单**密钥|
|VK_LSHIFT|**左 Shift**密钥|
|VK_MEDIA_NEXT_TRACK|(Windows)**下一曲目**密钥|
|VK_MEDIA_PLAY_PAUSE|(Windows)**播放/暂停媒体**密钥|
|VK_MEDIA_PREV_TRACK|(Windows)**上一曲目**密钥|
|VK_MEDIA_STOP|(Windows)**停止媒体**密钥|
|VK_MODECHANGE|(IME) 模式下更改请求|
|VK_NONCONVERT|(IME) 不转换|
|VK_OEM_1|(Windows)适用于美国标准键盘， **;:** 密钥|
|VK_OEM_102|(Windows)尖括号键或 RT 102 键键盘上的反斜杠键|
|VK_OEM_2|(Windows)适用于美国标准键盘， **/？** 密钥|
|VK_OEM_3|(Windows)适用于美国标准键盘， **`~** 密钥|
|VK_OEM_4|(Windows)适用于美国标准键盘， **[{** 密钥|
|VK_OEM_5|(Windows)适用于美国标准键盘， **\\ &#124;** 密钥|
|VK_OEM_6|(Windows)适用于美国标准键盘， **]}** 密钥|
|VK_OEM_7|(Windows)适用于美国标准键盘，单-单引号/双引号键|
|VK_OEM_COMMA|(Windows)适用于任何国家/地区 **，** 密钥|
|VK_OEM_MINUS|(Windows)适用于任何国家/地区**-** 密钥|
|VK_OEM_PERIOD|(Windows)适用于任何国家/地区， **。** 密钥|
|VK_OEM_PLUS|(Windows)适用于任何国家/地区**+** 密钥|
|VK_PACKET|(Windows)用于传递 Unicode 字符，如同它们是击键。|
|VK_RCONTROL|**右 Ctrl**密钥|
|VK_RMENU|**右菜单**密钥|
|VK_RSHIFT|**右 shift 组合键，** 密钥|
|VK_SLEEP|**计算机睡眠**密钥|
|VK_VOLUME_DOWN|(Windows)**调低音量**密钥|
|VK_VOLUME_MUTE|(Windows)**静音**密钥|
|VK_VOLUME_UP|(Windows)**调高音量**密钥|
|VK_XBUTTON1|(Windows)**X1**鼠标按钮|
|VK_XBUTTON2|(Windows)**X2**鼠标按钮|

## <a name="accelerator-key-association"></a>加速器键关联

很多时候，你希望某一菜单项和某一键盘组合可以发出相同的程序命令。 通过到菜单项和应用程序的快捷键对应表中的条目分配相同的资源标识符 (ID) 执行此操作。 接着你可以编辑该菜单项的标题，以显示快捷键的名称。 菜单项和快捷键的详细信息，请参阅[菜单命令](../windows/associating-a-menu-command-with-an-accelerator-key.md)。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[快捷键编辑器](../windows/accelerator-editor.md)<br/>