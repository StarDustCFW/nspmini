# nspmini
## Simple Lib code to Install nsp on any nro or app
* since Applet mode not have much memory some apps use NSP

### Posible uses
* install forwaders of NRO files
* install apps in nsp format and update them

## How to Use 
* type ``git clone https://github.com/StarDustCFW/nspmini``
* type ``make -C nspmini portlib`` to install has a port lib
* * to update use `git -C nspmini pull` & `make -C nspmini portlib`
* * or taking [a pre build](https://github.com/StarDustCFW/nspmini/actions) and copy to :
* * * windows ``C:\devkitPro\portlibs\switch``
* * * Linux ``/opt/devkitpro/portlibs/switch``

### On the makefile
* add the lib 
`LIBS += -lnsp`

### On your program code use 
```c++
#include "nspmini.hpp"
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

//DATA

//Get Title ID u64 format of latest
u64 m_tid = mini::GetTitleID();

//Get Title ID string format of latest
std::string tid = mini::GetTitleID_string();

//Get a list of all titles ids installed with nspmini
std::vector<u64> tidlist = mini::GetTitleID_vector();
```
Example
```c++
...
#include "nspmini.hpp"
int main(){
	//Install nsp
	mini::InstallSD("romfs:/myforwader.nsp");
	mini::InstallSD("sdmc:/myapp.nsp");
	
	//to launch the installed nsp from your app use:
	unsigned long long AppTitleID =  mini::GetTitleID();
	//AppTitleID is a u64 in hex like this 0x05B9DB505ABBE000
	appletRequestLaunchApplication (AppTitleID , NULL);
}
...
```
To install or update Nsp files



##  Used has Submodule
* type ``git submodule add https://github.com/StarDustCFW/nspmini``
* * to update use `git submodule update --recursive --init --remote --merge`
on the root of your repo
* Or just download and copy nspmini to your repo
* Also using `make release` to get only includes and lib
* * or taking [a pre build](https://github.com/StarDustCFW/nspmini/actions)


### On the makefile
* add include
`INCLUDES += nspmini/include `
* add lib 
`LIBS += -lnsp`
* add LIBDIR
` LIBDIRS	+= $(CURDIR)/nspmini`
* * use ``make -c nspmini`` to build the lib
* * or use `@$(MAKE) -C $(CURDIR)/nspmini/` on make file 



# Credits
* [Awoo-Installer](https://github.com/Huntereb/Awoo-Installer)
* [Adubbz-Tinfoil](https://github.com/Adubbz/Tinfoil)
