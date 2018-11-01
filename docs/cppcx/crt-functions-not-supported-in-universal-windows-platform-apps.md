---
title: 通用 Windows 平台应用中不支持的 CRT 函数
ms.date: 12/30/2016
ms.assetid: cbfc957d-6c60-48f4-97e3-1ed8526743b4
ms.openlocfilehash: 2de3edb11d65236f14c4c8fdf52fe6c855399dba
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50527681"
---
# <a name="crt-functions-not-supported-in-universal-windows-platform-apps"></a>通用 Windows 平台应用中不支持的 CRT 函数

生成通用 Windows 平台 (UWP) 应用时，许多 C 运行时 (CRT) 函数不可用。 在某些情况下，解决方法都是可用--例如，可以使用 Windows 运行时或 Win32 Api。 但是在其他情况下，CRT 函数被禁止使用，因为对应于它们的功能或支持 API 不适用于 UWP 应用。 若要查找的 Windows 运行时支持一种替代方法，请参阅[UWP 应用中的 Windows Api 的替代方法](/uwp/win32-and-com/alternatives-to-windows-apis-uwp)。

下表列出了在生成 UWP 应用时不可用的 CRT 函数，并指出了任何适用的解决方法。

## <a name="unsupported-crt-functions"></a>不支持的 CRT 函数

||||
|-|-|-|
|_beep _sleep _seterrormode|这些函数在以前版本的 CRT 中已过时。 此外，对应 Win32 API 不可用于 UWP 应用。|无解决方法。|
|chdir _chdrive getcwd|这些函数已过时或不是线程安全的。|使用 _chdir、_getcwd 及相关函数。|
|_cgets _cgets_s _cgetws _cgetws_s _cprintf _cprintf_l _cprintf_p _cprintf_p_l _cprintf_s _cprintf_s_l _cputs _cputws _cscanf _cscanf_l _cscanf_s _cscanf_s_l _cwait _cwprintf _cwprintf_l _cwprintf_p _cwprintf_p_l _cwprintf_s _cwprintf_s_l _cwscanf _cwscanf_l _cwscanf_s _cwscanf_s_l _vcprintf _vcprintf_l _vcprintf_p _vcprintf_p_l _vcprintf_s _vcprintf_s_l _vcwprintf _vcwprintf_l _vcwprintf_p _vcwprintf_p_l _vcwprintf_s _vcwprintf_s_l _getch _getch_nolock _getche _getche_nolock _getwch _getwch_nolock _getwche _getwche_nolock _putch _putch_nolock _putwch _putwch_nolock _ungetch _ungetch_nolock _ungetwch _ungetwch_nolock _kbhit kbhit putch cgets cprintf cputs cscanf cwait getch getche ungetch|这些函数用于直接从控制台读取和写入控制台。 UWP 应用仅限 GUI；它们不支持控制台。|无解决方法。|
|getpid|此函数已过时。|使用 _getpid 或 Win32 API `GetCurrentProcessId()`。|
|_getdiskfree|不可用。|使用 Win32 API `GetDiskFreeSpaceExW()`。|
|_getdrive _getdrives|对应 API 不可用于 UWP 应用。|无解决方法。|
|_inp _inpd _inpw _outp _outpd _outpw inp inpd inpw outp outpd outpw|UWP 应用中不支持端口 IO。|无解决方法。|
|_ismbcalnum _ismbcalnum_l _ismbcalpha _ismbcalpha_l _ismbcdigit _ismbcdigit_l _ismbcgraph _ismbcgraph_l _ismbchira _ismbchira_l _ismbckata _ismbckata_l _ismbcl0 _ismbcl0_l _ismbcl1 _ismbcl1_l _ismbcl2 _ismbcl2_l _ismbclegal _ismbclegal_l _ismbclower _ismbclower_l _ismbcprint _ismbcprint_l _ismbcpunct _ismbcpunct_l _ismbcspace _ismbcspace_l _ismbcsymbol _ismbcsymbol_l _ismbcupper _ismbcupper_l _mbbtombc _mbbtombc_l _mbbtype _mbbtype_l _mbccpy _mbccpy_l _mbccpy_s _mbccpy_s_l _mbcjistojms _mbcjistojms_l _mbcjmstojis _mbcjmstojis_l _mbclen _mbclen_l _mbctohira _mbctohira_l _mbctokata _mbctokata_l _mbctolower _mbctolower_l _mbctombb _mbctombb_l _mbctoupper _mbctoupper_l _mbsbtype _mbsbtype_l _mbscat _mbscat_l _mbscat_s _mbscat_s_l _mbschr _mbschr_l _mbscmp _mbscmp_l _mbscoll _mbscoll_l _mbscpy _mbscpy_l _mbscpy_s _mbscpy_s_l _mbscspn _mbscspn_l _mbsdec _mbsdec_l _mbsicmp _mbsicmp_l _mbsicoll _mbsicoll_l _mbsinc _mbsinc_l _mbslen _mbslen_l _mbslwr _mbslwr_l _mbslwr_s _mbslwr_s_l _mbsnbcat _mbsnbcat_l _mbsnbcat_s _mbsnbcat_s_l _mbsnbcmp _mbsnbcmp_l _mbsnbcnt _mbsnbcnt_l _mbsnbcoll _mbsnbcoll_l _mbsnbcpy _mbsnbcpy_l _mbsnbcpy_s _mbsnbcpy_s_l _mbsnbicmp _mbsnbicmp_l _mbsnbicoll _mbsnbicoll_l _mbsnbset _mbsnbset_l _mbsnbset_s _mbsnbset_s_l _mbsncat _mbsncat_l _mbsncat_s _mbsncat_s_l _mbsnccnt _mbsnccnt_l _mbsncmp _mbsncmp_l _mbsncoll _mbsncoll_l _mbsncpy _mbsncpy_l _mbsncpy_s _mbsncpy_s_l _mbsnextc _mbsnextc_l _mbsnicmp _mbsnicmp_l _mbsnicoll _mbsnicoll_l _mbsninc _mbsninc_l _mbsnlen _mbsnlen_l _mbsnset _mbsnset_l _mbsnset_s _mbsnset_s_l _mbspbrk _mbspbrk_l _mbsrchr _mbsrchr_l _mbsrev _mbsrev_l _mbsset _mbsset_l _mbsset_s _mbsset_s_l _mbsspn _mbsspn_l _mbsspnp _mbsspnp_l _mbsstr _mbsstr_l _mbstok _mbstok_l _mbstok_s _mbstok_s_l _mbsupr _mbsupr_l _mbsupr_s _mbsupr_s_l is_wctype|UWP 应用中不支持多字节字符串。|改为使用 Unicode 字符串。|
|_pclose _pipe _popen _wpopen|管道功能不可用于 UWP 应用。|无解决方法。|
|_resetstkoflw|支持 Win32 API 不可用于 UWP 应用。|无解决方法。|
|_getsystime _setsystime|这些是以前 CRT 版本中的已过时 API。 此外，用户无法在 UWP 应用中设置系统时间，因为缺少权限。|若要只获取系统时间，请使用 Win32 API `GetSystemTime`。 无法设置系统时间。|
|_environ _putenv _putenv_s _searchenv _searchenv_s _dupenv_s _wputenv _wputenv_s _wsearchenv getenv getenv_s putenv _wdupenv_s _wenviron _wgetenv _wgetenv_s _wsearchenv_s tzset|环境变量不可用于 UWP 应用。|无解决方法。 若要设置时区，请使用 _tzset。|
|_loaddll _getdllprocaddr _unloaddll|这些是以前 CRT 版本中的已过时函数。 此外，用户无法加载 DLL（同一个应用程序包中的 DLL 除外）。|使用 Win32 API `LoadPackagedLibrary`、 `GetProcAddress`和 `FreeLibrary` 加载和使用打包的 DLL。|
|_wexecl _wexecle _wexeclp _wexeclpe _wexecv _wexecve _wexecvp _wexecvpe _execl _execle _execlp _execlpe _execv _execve _execvp _execvpe _spawnl _spawnle _spawnlp _spawnlpe _spawnv _spawnve _spawnvp _spawnvpe _wspawnl _wspawnle _wspawnlp _wspawnlpe _wspawnv _wspawnve _wspawnvp _wspawnvpe _wsystem execl execle execlp execlpe execv execve execvp execvpe spawnl spawnle spawnlp spawnlpe spawnv spawnve spawnvp spawnvpe system|该功能在 UWP 应用中不可用。 UWP 应用无法调用另一个 UWP 应用或桌面应用。|无解决方法。|
|_heapwalk _heapadd _heapchk _heapset _heapused|这些函数通常用于处理堆。 但是，UWP 应用中不支持对应 Win32 API。 而且，应用无法再创建或使用专用堆。|无解决方法。 但是， `_heapwalk` 在 DEBUG CRT 中可用（仅用于进行调试）。 这些不能中上传到 Microsoft Store 的应用程序使用。|

以下函数在 UWP 应用的 CRT 中可用，但仅当不能使用对应 Win32 或 Windows 运行时 Api 时，才应使用 — 例如，当您要移植大型基本代码

|||
|-|-|
|单字节字符串函数（例如， `strcat`、 `strcpy`、 `strlwr`等）。|使 UWP 应用严格遵循 Unicode 因为所有 Win32 Api 和 Windows 运行时 Api 公开都使用的 Unicode 字符仅设置。  保留了单字节函数，以便用于移植大型基本代码，但在其他情况下应避免使用，并且应尽可能改用对应的宽字符函数。|
|流 IO 和低级文件 IO 函数（例如， `fopen`、 `open`等）。|这些函数是同步的，不推荐用于 UWP 应用。 在 UWP 应用中，使用异步 API 打开、读取和写入文件，以防止锁定 UI 线程。 这类 API 的示例是在 `Windows::Storage::FileIO` 类中的一个。|

## <a name="windows-8x-store-apps-and-windows-phone-8x-apps"></a>Windows 8.x 应用商店应用和 Windows Phone 8.x 应用

除了前面提到的 API 之外，以下 API 在 Windows 8.x 应用商店应用和 Windows Phone 8.x 应用中不可用。

||||
|-|-|-|
|_beginthread _beginthreadex _endthread _endthreadex|线程处理 Win32 API 在 Windows 8.x 应用商店应用中不可用。|改用 `Windows Runtime Windows::System::Threading::ThreadPool` 或 `concurrency::task` 。|
|_chdir _wchdir _getcwd _getdcwd _wgetcwd _wgetdcwd|工作目录的概念不适用于 Windows 8.x 应用商店应用。|改用完整路径。|
|_getpid|此函数在以前版本的 CRT 中已过时。|使用 Win32 API `GetCurrentProcessId()`|
|_isleadbyte_l _ismbbalnum, _ismbbalnum_l, _ismbbalpha, _ismbbalpha _ismbbalpha_l _ismbbgraph _ismbbgraph_l _ismbbkalnum _ismbbkalnum_l _ismbbkana _ismbbkana_l _ismbbkprint _ismbbkprint_l _ismbbkpunct _ismbbkpunct_l _ismbblead _ismbblead_l _ismbbprint _ismbbprint_l _ismbbpunct _ismbbpunct_l _ismbbtrail _ismbbtrail_l _ismbslead _ismbslead_l _ismbstrail _ismbstrail_l _mbsdup isleadbyte|Windows 8.x 应用商店应用中不支持多字节字符串。|改为使用 Unicode 字符串。|
|_tzset|环境变量不可用于 Windows 8.x 应用商店应用。|无解决方法。|
|_get_heap_handle、_heapmin|Windows 8.x 应用商店应用中不支持对应 Win32 API。 而且，应用无法再创建专用堆。|无解决方法。 但是， `_get_heap_handle` 在 DEBUG CRT 中可用（仅用于进行调试）。|