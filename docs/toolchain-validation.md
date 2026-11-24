# BOF1R toolchain validation

The target platform is Windows x64. This check used GBARecomp revision `889fb72b6e3277d670e2cc7b75c5a47b09b7bd59` and its original CPU timing fixture. The fixture exercises ARM and Thumb code in cartridge and work RAM. [GBARecomp revision](https://github.com/mstan/gbarecomp/tree/889fb72b6e3277d670e2cc7b75c5a47b09b7bd59) · [Timing fixture source](https://github.com/mstan/gbarecomp/tree/889fb72b6e3277d670e2cc7b75c5a47b09b7bd59/tests/timing)

| Check | Result |
| --- | --- |
| Windows x64 recompiler | Built `gba_recompile.exe` and verified its PE32+ x86-64 format. |
| Windows x64 native fixture | Built `timing_rom_tests.exe` from generated C++ and verified its PE32+ x86-64 format. Wine initialization blocked execution in this environment. |
| Linux x64 reference tests | `native_region_contract` and `timing_rom_tests` both passed. |

The Windows cross-build used CMake 3.31.10 and LLVM-MinGW 20261117. GNU ARM binutils 2.44 assembled the fixture, which matched the SHA-1 pinned in the upstream test configuration. The Linux recompiler generated the C++ used by the Windows fixture build. [LLVM-MinGW release](https://github.com/mstorsjo/llvm-mingw/releases/tag/20261117)

The game build and integration of the requested ROM hack are pending. This check used upstream test code only. [Requested ROM hack](https://www.romhacking.net/hacks/7597/)
