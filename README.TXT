Within Visual Studio 2013 using the wizards I have created a bare .NET 4.5 WPF C# application 
which also has a C++/CLI class library. 

When I run the application on my Windows 8 (or Windows 10) development machine 
the app runs just fine. 

However when I run it on a clean Windows 7 machine it crashes 
the moment the C# tries to instantiate an object defined in the C++/CLI class library. 

I have not changed anything in the options, I have just used the wizards to create a C# WPF app and 
a C++ CLR class library, and I have created a ref class in the library, 
and I tried to instantiate the ref class from a button click handler in the WPF window from the C# app.
 


If I attach WinDbg to the TestWPF process once I hit the Button the application crashes and WinDbg reports the following exception

ModLoad: 5f890000 5f8a2000   ClassLibrary1.dll
ModLoad: 047e0000 047f2000   ClassLibrary1.dll
ModLoad: 5f890000 5f8a2000   C:\Temp\TestWpf\ClassLibrary1.dll
(1314.694): C++ EH exception - code e06d7363 (first chance)
(1314.694): C++ EH exception - code e06d7363 (first chance)
(1314.694): C++ EH exception - code e06d7363 (first chance)
(1314.694): C++ EH exception - code e06d7363 (first chance)
(1314.694): C++ EH exception - code e06d7363 (first chance)
(1314.694): CLR exception - code e0434352 (first chance)
(1314.694): C++ EH exception - code e06d7363 (first chance)
ModLoad: 5f7b0000 5f881000   C:\Windows\Microsoft.NET\Framework\v4.0.30319\diasymreader.dll
(1314.694): CLR exception - code e0434352 (!!! second chance !!!)
eax=0024d708 ebx=00000005 ecx=00000005 edx=00000000 esi=0024d7c4 edi=00000001
eip=7704c52f esp=0024d708 ebp=0024d758 iopl=0         nv up ei pl nz ac po nc
cs=0023  ss=002b  ds=002b  es=002b  fs=0053  gs=002b             efl=00000212
KERNELBASE!RaiseException+0x58:
7704c52f c9              leave





Here is the full WinDbg log


Microsoft (R) Windows Debugger Version 10.0.10586.567 X86
Copyright (c) Microsoft Corporation. All rights reserved.

*** wait with pending attach
Symbol search path is: srv*
Executable search path is: 
ModLoad: 00390000 00398000   C:\Temp\TestWpf\TestWPF.exe
ModLoad: 77640000 777c0000   C:\Windows\SysWOW64\ntdll.dll
ModLoad: 68920000 6896a000   C:\Windows\SYSTEM32\MSCOREE.DLL
ModLoad: 765d0000 766e0000   C:\Windows\syswow64\KERNEL32.dll
ModLoad: 77040000 77087000   C:\Windows\syswow64\KERNELBASE.dll
ModLoad: 75c50000 75cf1000   C:\Windows\syswow64\ADVAPI32.dll
ModLoad: 76a90000 76b3c000   C:\Windows\syswow64\msvcrt.dll
ModLoad: 76b40000 76b59000   C:\Windows\SysWOW64\sechost.dll
ModLoad: 76820000 76910000   C:\Windows\syswow64\RPCRT4.dll
ModLoad: 74f90000 74ff0000   C:\Windows\syswow64\SspiCli.dll
ModLoad: 74f80000 74f8c000   C:\Windows\syswow64\CRYPTBASE.dll
ModLoad: 688a0000 6891e000   C:\Windows\Microsoft.NET\Framework\v4.0.30319\mscoreei.dll
ModLoad: 76570000 765c7000   C:\Windows\syswow64\SHLWAPI.dll
ModLoad: 77090000 77120000   C:\Windows\syswow64\GDI32.dll
ModLoad: 76f40000 77040000   C:\Windows\syswow64\USER32.dll
ModLoad: 76a80000 76a8a000   C:\Windows\syswow64\LPK.dll
ModLoad: 769a0000 76a3d000   C:\Windows\syswow64\USP10.dll
ModLoad: 75f70000 75fd0000   C:\Windows\system32\IMM32.DLL
ModLoad: 77120000 771ec000   C:\Windows\syswow64\MSCTF.dll
ModLoad: 68200000 6889d000   C:\Windows\Microsoft.NET\Framework\v4.0.30319\clr.dll
ModLoad: 68120000 681f7000   C:\Windows\system32\MSVCR120_CLR0400.dll
ModLoad: 628c0000 6392b000   C:\Windows\assembly\NativeImages_v4.0.30319_32\mscorlib\d1265d6159ea876f9d63ea4c1361b587\mscorlib.ni.dll
ModLoad: 76410000 7656c000   C:\Windows\syswow64\ole32.dll
ModLoad: 72400000 72480000   C:\Windows\system32\uxtheme.dll
ModLoad: 67780000 6811d000   C:\Windows\assembly\NativeImages_v4.0.30319_32\System\85cfc067e323f00f43254de906523a60\System.ni.dll
ModLoad: 645e0000 6499c000   C:\Windows\assembly\NativeImages_v4.0.30319_32\WindowsBase\1f8f8a649f61763babca9ab483ed8a60\WindowsBase.ni.dll
ModLoad: 72880000 72897000   C:\Windows\system32\CRYPTSP.dll
ModLoad: 72840000 7287b000   C:\Windows\system32\rsaenh.dll
ModLoad: 63b50000 645d3000   C:\Windows\assembly\NativeImages_v4.0.30319_32\PresentationCore\754a44b390f7eea7483d47206622a926\PresentationCore.ni.dll
ModLoad: 616d0000 628b4000   C:\Windows\assembly\NativeImages_v4.0.30319_32\Presentatio5ae0f00f#\cf6c48ebc32475e49b3a7dec1e85f675\PresentationFramework.ni.dll
ModLoad: 675b0000 6777c000   C:\Windows\assembly\NativeImages_v4.0.30319_32\System.Xaml\abde200e01cfd34122c55783bfe5dc02\System.Xaml.ni.dll
ModLoad: 73660000 73796000   C:\Windows\system32\dwrite.dll
ModLoad: 67410000 675a8000   C:\Windows\Microsoft.NET\Framework\v4.0.30319\WPF\wpfgfx_v0400.dll
ModLoad: 75d00000 75d8f000   C:\Windows\syswow64\OLEAUT32.dll
ModLoad: 63a80000 63b41000   C:\Windows\Microsoft.NET\Framework\v4.0.30319\WPF\PresentationNative_v0400.dll
ModLoad: 63a00000 63a7d000   C:\Windows\Microsoft.NET\Framework\v4.0.30319\clrjit.dll
ModLoad: 673f0000 67402000   C:\Windows\Microsoft.NET\Framework\v4.0.30319\nlssorting.dll
ModLoad: 71dc0000 71dd3000   C:\Windows\system32\dwmapi.dll
ModLoad: 71980000 71b43000   C:\Windows\system32\d3d9.dll
ModLoad: 74eb0000 74eb9000   C:\Windows\system32\VERSION.dll
ModLoad: 72180000 72186000   C:\Windows\system32\d3d8thk.dll
ModLoad: 60850000 616cf000   C:\Windows\system32\nvd3dum.dll
ModLoad: 77610000 77615000   C:\Windows\syswow64\PSAPI.DLL
ModLoad: 74ff0000 75c3b000   C:\Windows\system32\Shell32.dll
ModLoad: 63980000 639f1000   C:\Windows\assembly\NativeImages_v4.0.30319_32\Presentatio1c9175f8#\ae38d37f0cd997d86dbc329d0470c38f\PresentationFramework.Aero.ni.dll
ModLoad: 72920000 7292d000   C:\Windows\system32\WtsApi32.dll
ModLoad: 72ef0000 72f19000   C:\Windows\system32\WINSTA.dll
ModLoad: 76910000 76993000   C:\Windows\syswow64\CLBCatQ.DLL
ModLoad: 63960000 63975000   C:\Windows\Microsoft.NET\Framework\v4.0.30319\WPF\PenIMC.dll
ModLoad: 72910000 7291e000   C:\Windows\system32\RpcRtRemote.dll
ModLoad: 73f80000 74075000   C:\Windows\system32\PROPSYS.dll
ModLoad: 724a0000 7263e000   C:\Windows\WinSxS\x86_microsoft.windows.common-controls_6595b64144ccf1df_6.0.7601.18837_none_41e855142bd5705d\comctl32.dll
ModLoad: 74e20000 74e41000   C:\Windows\system32\ntmarta.dll
ModLoad: 767d0000 76815000   C:\Windows\syswow64\WLDAP32.dll
ModLoad: 761f0000 761fb000   C:\Windows\syswow64\profapi.dll
ModLoad: 762a0000 763eb000   C:\Windows\SysWOW64\urlmon.dll
ModLoad: 76a70000 76a74000   C:\Windows\syswow64\api-ms-win-downlevel-ole32-l1-1-0.dll
ModLoad: 75da0000 75da4000   C:\Windows\syswow64\api-ms-win-downlevel-shlwapi-l1-1-0.dll
ModLoad: 75d90000 75d95000   C:\Windows\syswow64\api-ms-win-downlevel-advapi32-l1-1-0.dll
ModLoad: 76250000 76254000   C:\Windows\syswow64\api-ms-win-downlevel-user32-l1-1-0.dll
ModLoad: 75c40000 75c44000   C:\Windows\syswow64\api-ms-win-downlevel-version-l1-1-0.dll
ModLoad: 761e0000 761e3000   C:\Windows\syswow64\api-ms-win-downlevel-normaliz-l1-1-0.dll
ModLoad: 75f60000 75f63000   C:\Windows\syswow64\normaliz.DLL
ModLoad: 76b60000 76d92000   C:\Windows\syswow64\iertutil.dll
ModLoad: 75fd0000 761dd000   C:\Windows\syswow64\WININET.dll
ModLoad: 763f0000 76407000   C:\Windows\syswow64\USERENV.dll
ModLoad: 72490000 72498000   C:\Windows\system32\Secur32.dll
ModLoad: 76da0000 76f3d000   C:\Windows\syswow64\SETUPAPI.dll
ModLoad: 76a40000 76a67000   C:\Windows\syswow64\CFGMGR32.dll
ModLoad: 77220000 77232000   C:\Windows\syswow64\DEVOBJ.dll
ModLoad: 71da0000 71db2000   C:\Windows\system32\MPR.dll
ModLoad: 72130000 7213d000   C:\Program Files (x86)\Common Files\Microsoft Shared\Ink\tpcps.dll
ModLoad: 721e0000 72205000   C:\Windows\system32\powrprof.dll
ModLoad: 60710000 60843000   C:\Program Files (x86)\NVIDIA Corporation\3D Vision\nvSCPAPI.dll
ModLoad: 63940000 63957000   C:\Windows\system32\msctfui.dll
ModLoad: 606e0000 60710000   C:\Windows\assembly\NativeImages_v4.0.30319_32\UIAutomationTypes\232495ea0368dada2d208c51f0e5349c\UIAutomationTypes.ni.dll
ModLoad: 60650000 606dc000   C:\Windows\system32\UIAutomationCore.dll
ModLoad: 73c20000 73c5c000   C:\Windows\system32\OLEACC.dll
(1314.f54): Break instruction exception - code 80000003 (first chance)
eax=7ef91000 ebx=00000000 ecx=00000000 edx=776dffea esi=00000000 edi=00000000
eip=7765000c esp=0632fec4 ebp=0632fef0 iopl=0         nv up ei pl zr na pe nc
cs=0023  ss=002b  ds=002b  es=002b  fs=0053  gs=002b             efl=00000246
ntdll!DbgBreakPoint:
7765000c cc              int     3
0:013> g
ModLoad: 71e10000 71e42000   C:\Windows\SysWOW64\WINMM.dll
ModLoad: 5f890000 5f8a2000   ClassLibrary1.dll
ModLoad: 047e0000 047f2000   ClassLibrary1.dll
ModLoad: 5f890000 5f8a2000   C:\Temp\TestWpf\ClassLibrary1.dll
(1314.694): C++ EH exception - code e06d7363 (first chance)
(1314.694): C++ EH exception - code e06d7363 (first chance)
(1314.694): C++ EH exception - code e06d7363 (first chance)
(1314.694): C++ EH exception - code e06d7363 (first chance)
(1314.694): C++ EH exception - code e06d7363 (first chance)
(1314.694): CLR exception - code e0434352 (first chance)
(1314.694): C++ EH exception - code e06d7363 (first chance)
ModLoad: 5f7b0000 5f881000   C:\Windows\Microsoft.NET\Framework\v4.0.30319\diasymreader.dll
(1314.694): CLR exception - code e0434352 (!!! second chance !!!)
eax=0024d708 ebx=00000005 ecx=00000005 edx=00000000 esi=0024d7c4 edi=00000001
eip=7704c52f esp=0024d708 ebp=0024d758 iopl=0         nv up ei pl nz ac po nc
cs=0023  ss=002b  ds=002b  es=002b  fs=0053  gs=002b             efl=00000212
KERNELBASE!RaiseException+0x58:
7704c52f c9              leave
