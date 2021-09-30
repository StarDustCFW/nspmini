# mininsp
### How to Use 
place nspmini on the root of 
INCLUDES	+=	nspmini/include

On your program use #include "sdInstall.hpp"
use 
```c++
//To install a single File
mini::InstallSD(std::string nsp);
	
//Or this to install a vector of files
std::vector<std::filesystem::path> ourTitleList={
	std::filesystem::path(std::string nsp),
	std::filesystem::path(std::string nsp2)
}; 
mini::installNspFromFile(ourTitleList, 0);// 0 is SDcard (default), 1 is BuildInUser 

```
