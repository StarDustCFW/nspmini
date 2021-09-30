# mininsp c++
## Simple Lib code to Install nsp on any nro or app
* since Applet mode not have much memory some apps use NSP

### Posible uses
* install forwaders of NRO files
* install apps in nsp format and update them

## How to Use 
* type ``git submodule add https://github.com/StarDustCFW/mininsp``
* * to update use `it submodule update --recursive --remote --merge`
on the root of your repo
* Or just download and copy mininsp to your repo


### On the makefile
* add include
`INCLUDES += nspmini/include `
* add lib 
`LIBS += -lnsp`
* add LIBDIR
` LIBDIRS	+= $(CURDIR)/nspmini`
* * use ``make -c mininspn`` to build the lib
* * or use `@$(MAKE) -C $(CURDIR)/nspmini/` on make file 

### On your program use 
```c++
#include "sdInstall.hpp"
```
And
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
Example
```c++
...
#include "sdInstall.hpp"
int main(){

	mini::InstallSD("romfs:/myforwader.nsp");
	mini::InstallSD("sdmc:/myapp.nsp");
}
...
```
To install or update Nsp files
### TIP
to launch the installed nsp from your app  use
```c++
unsigned long long AppTitleID = 0x05B9DB505ABBE000;//replace this with your App id
appletRequestLaunchApplication (AppTitleID , NULL);
```


# Credits
* [Awoo-Installer](https://github.com/Huntereb/Awoo-Installer)
* [Adubbz-Tinfoil](https://github.com/Adubbz/Tinfoil)
