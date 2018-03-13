# C++ Snippets
## File
* Append a file
```c++
#include <fstream>

std::ofstream myfile;
myfile.open ("my_file_path", std::fstream::app);
myfile << "data\n";
myfile.close();
```

## Time
* Get a human readable timestamp
  * before C++ 11 ([time formats](http://en.cppreference.com/w/cpp/chrono/c/strftime))
```c++
#include <time.h>

time_t now = ::time(0);
struct tm  tstruct;
char buf[100];

tstruct = *localtime(&now);
strftime(buf, sizeof(buf), "%Y-%m-%d %X", &tstruct);
```
