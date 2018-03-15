# Snippets
## File
### Append a file

|C++|Python|
|-|-|
|#include &lsaquo;fstream&rsaquo;<br><br>std::ofstream file;<br>file.open ("path", std::fstream::app);<br>file << "data\n";<br>file.close();<br>|with open("path", "a") as file:<br>&nbsp;file.write("data\n")|

## Time
### Get a human readable timestamp
* Before C++ 11 [time formats](http://en.cppreference.com/w/cpp/chrono/c/strftime)
* Python [time formats](https://docs.python.org/2/library/datetime.html#strftime-and-strptime-behavior)

|pre C++ 11|
|-|
|#include &lsaquo;time.h&rsaquo;<br><br>time_t now = ::time(0);<br>struct tm  tstruct;<br>char buf[100];<br><br>tstruct = *localtime(&now);<br>strftime(buf, sizeof(buf), "%Y-%m-%d %X", &tstruct);|

### Measure performances

|Python|
|-|
|import timeit<br><br>start = timeit.default_timer()<br>...<br>end = timeit.default_timer()<br>print( "Completed in {0:.3f}s".format(end - start) )<pr>|
