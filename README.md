# reverseNote
### 逆向笔记

#### 恢复符号表只能针对单一架构恢复，所以在恢复之前查看MachO文件是否单一架构，如果不是，则先拆分成单一架构，再恢复符号表
> $lipo -info WeChat
Non-fat file: WeChat is architecture: arm64 armv7

#### 如果是多架构，则拆分
> $lipo WeChat -thin arm64 -output WeChat_arm64

#### 获取block符号表文件 block_symbol.json

#### 在ida中执行脚本文件 ida_search_block.py
￼![xxx](https://raw.githubusercontent.com/devhusky/reverseNote/master/images/1563179714597.jpg)

#### 恢复符号表（包含block符号表）
> $./restore-symbol  WeChat -o WeChat_temp -j block_symbol.json
