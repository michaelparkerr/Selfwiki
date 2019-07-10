```bash
82  sudo apt-get install gdb
   83  sudo apt-get install peda
   84  ls
   85  cd protostar
   86  ls
   87  ./
   88  ./stack0
   89  chmod 777 stack0
   90  ./stack0
   91  stack0
   92  ls
   93  stack0
   94  ./stack0
   95  sudo apt-get install ia32-libs
   96  sudo dpkg --add-architecture i386
   97  sudo apt-get update
   98  sudo apt-get install libc6:i386 libncurses5:i386 libstdc++6:i386 zlib1g:i386
   99  ./stack0
  100  gdb stack0
  101  git clone https://github.com/longld/peda.git ~/peda
  102  echo "source ~/peda/peda.py" >> ~/.gdbinit
  103  gdb stack0

```

