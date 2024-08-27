# logz

a header only lite logging library for C++(11+)

- posix compliant
- header only
- no dependencies
- thread safe
- ratationally resizable log file

# compile

g++ example.cpp -o logz

# Usage

refer to example.cpp

see the comments for more details:
```c++

#include "logz.hpp"

int main() {

    yy::logz::conf c{ 0 };

    c.dir        = "./";//store the log in dir
    c.prefix     = "test";//log name: test.log
    c.rot_size   = 1024;//rotate when log size reaches 1024 bytes
    c.time_fmt   = 0;//use local time or milliseconds
    c.use_stdout = 1;//tee to stdout
    c.in_place   = 1;//in-place rotation: previous log file will be named as test.log.1and so on

    LOGZ_INIT( c );//initialize logger

    int i = 100;
    while ( i-- ) {
        LOGZ_FMT( "put,>>>>>>> i = %d", i );//log message with format string
        sleep( 1 );
    }

    LOGZ_CLOSE();//close logger

    return 0;
}

```
# snapshot

![logger](https://github.com/user-attachments/assets/acafbdd6-eb68-4c76-a53c-5f7b4bfa3114)

# author

wechat: 371536435
email: yzbit@outlook.com
